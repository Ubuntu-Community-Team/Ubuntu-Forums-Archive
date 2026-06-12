---
title: "Project Euler Problem 79"
date: 2008-08-03
forum: Programming Talk
---

### Post by spadewarrior on 2008-08-03
Hi guys n gals.

I've found this problem pretty difficult. 

[http://projecteuler.net/index.php?section=problems&id=79](http://projecteuler.net/index.php?section=problems&id=79)

I've put the first, second and third digit of each entry into separate lists. I then made a dictionary for each list to show where each 0 - 9 number appeared appeared the most often and then made a function that (I hoped) arranged them into the correct order.

Is this the right idea? Or am I going about it wrongly? 

I can post my code if you like. It's pretty dirty though.

Thanks.

---

### Post by KMuchane on 2008-08-04
Hi ,
This is one the few I solved without any code, well almost. And I am just a regular guy!  If you take a number like 319 you notice that 3 comes before 1 and 9 ,note that somewhere  as for 680, 6 precedes both 8 and 0, continue this way until you have the order of all the digits, trust me it will take you about 5 minutes. Good luck!

---

### Post by spadewarrior on 2008-08-04
Yeah, that's what I thought of doing too, but I want to do it in code.

---

### Post by Lster on 2008-08-04
I solved this one by analysis too.

I would make the assumption that all digits are distinct to begin with - this simplifies the working hugely. It also allows you to assume the length is &#8804; 10.

Here's my guess at a reasonably fast algorithm:

[LIST=1]
[*]Discover the set of different digits that are avaiable. Store these in an alphabet set.
[*]Make an empty array of the same length as the set. This will be used to store what each character could be.
[*]Go through each of the 50 lines removing any of the digits that appear in any position other than first character.
[*]Remove the one remaining digit from each of the lines so that some are shorter.
[*]Repeat the same tactic (from step 3) for the all the other digits. Gradually you will get and array with each element a list of all possible digits it could be.
[*]Simply enumerate the array, checking all possibilities, and the correct answer *should* be found!
[/LIST]

This should work but it relies of heuristics rather than solid algorithmics. Thinking about it further, a possibly faster algorithm would be to simply do a recursive branch-trimming algorithm. As each permutation is generated, it can be checked to see if it is possible.

---

### Post by Lster on 2008-08-04
Yes, my second algorithm using tree-trimming works exceedingly well! I managed to obtain the answer that way in ~40ms with Python.

Here's the specifics:

[LIST=1]
[*]Parse the log file for quick access. Store all the different digits in a set, alpha.
[*]Go through each permutation of alpha checking if the first few digits are possible given the data in the log.
[*]If it is possible and all digits have been used, this is *an* answer. For the challenge given, there is only one distinct answer so... :KS
[/LIST]

Code requests are welcome but I'd rather not post it publicly (to stop cheating). ;)

Lster

---

### Post by Kadrus on 2008-08-04
[PHP]import Data.Char (digitToInt, intToDigit)
import Data.Graph (buildG, topSort)
import Data.List (intersect)
 
p79 file= 
    (+0)$read . intersect graphWalk $ usedDigits
    where
    usedDigits = intersect "0123456789" $ file
    edges = concat . map (edgePair . map digitToInt) . words $ file
    graphWalk = map intToDigit . topSort . buildG (0, 9) $ edges
    edgePair [x, y, z] = [(x, y), (y, z)]
    edgePair _         = undefined
 
problem_79 = do
    f<-readFile  "keylog.txt"
    print $p79 f
[/PHP]

---

### Post by Lster on 2008-08-04
Umm... Isn't that from:

[http://www.haskell.org/haskellwiki/Euler_problems/71_to_80](http://www.haskell.org/haskellwiki/Euler_problems/71_to_80)

I *think* spadewarrior is using Python anyway.

---

### Post by Kadrus on 2008-08-04
> **Lster said:**
> Umm... Isn't that from:

[http://www.haskell.org/haskellwiki/Euler_problems/71_to_80](http://www.haskell.org/haskellwiki/Euler_problems/71_to_80)

I *think* spadewarrior is using Python anyway.

Yeah it is,it just needs to be ported.
found this: [http://pyeuler.wikidot.com/](http://pyeuler.wikidot.com/)
although it stops at prob 40

---

### Post by Lster on 2008-08-04
Well, since cheating is as simple as getting a Haskell compiler, here is my code:

[PHP]
#Code available with request.
[/PHP]

---

### Post by Martin Witte on 2008-08-04
> **Lster said:**
> 

[LIST=1]
[*]Parse the log file for quick access. Store all the different digits in a set, alpha.
[*]Go through each permutation of alpha checking if the first few digits are possible given the data in the log.
[*]If it is possible and all digits have been used, this is *an* answer. For the challenge given, there is only one distinct answer so... :KS
[/LIST]


Here's a variation using your algorithm
```

#!/usr/bin/env python
s = set()

f = open('p79.txt')
for i in f:
	for j in i[0], i[1], i[2]:
		s.add(int(j))

l = list(s)

def all_perms(l):
	if len(l) <=1:
		yield l
	else:
		for perm in all_perms(l[1:]):
			for i in range(len(perm)+1):
				yield perm[:i] + l[0:1] + perm[i:]
k = []
for i in open('p79.txt'):
	k.append([int(j) for j in i[0], i[1], i[2]])

for i in all_perms(l):
	n = 0
	for j in k:
		a = i.index(j[0])
		b = i.index(j[1])
		c = i.index(j[2])
		if not a < b < c:
			break
		else:
			n+=1
		if n == len(k):
			print i

```

where I saved the list of numbers in file called 'p79.txt'

---

