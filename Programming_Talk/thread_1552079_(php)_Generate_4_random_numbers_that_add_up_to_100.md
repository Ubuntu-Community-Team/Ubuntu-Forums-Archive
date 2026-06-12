---
title: "(php) Generate 4 random numbers that add up to 100?"
date: 2010-08-13
forum: Programming Talk
---

### Post by Johnsie on 2010-08-13
Well, I guess they wont be completely random, but I need to generate 4 randomish numbers that add up to exactly 100. Are there any mathematical geniuses that know how to do this in php?

---

### Post by Hellkeepa on 2010-08-13
HELLo!

Hmm.. I think I would have gone for something like this:
[php]// Initialize variables for later use.
$Target = 100;
$Nums = array ();
$Sum = 0;

// Get three random numbers, the last is found by simple substraction.
for ($Run = 3; $Run; --$Run) {
    // Make sure that the max random value is no bigger than $Total-1*remaining.
    $Max = $Target - $Sum - $Run;

    // Get the randum number, and add it to the array.
    // Also add the number to the sum used to calculate the max value.
    $Sum += $Nums[] = mt_rand (1, $Max);
}

// Add the final number.
$Nums[] = $Target - $Sum;
[/php]
Note that I haven't tested this, but it should work as specified.

Happy codin'!

---

### Post by robots.jpg on 2010-08-13
Quick question for anyone with some comp-sci/math background:

I was comparing the results from the posted method and the first one I thought of, and the distribution of the results is very different.  For example, I'm much less likely to ever see "extreme" combinations like (97,1,1,1).  What I did was take three unique, random numbers between 1 and 99 inclusive (n1, n2, n3) sorted by value, and used them to generate the four numbers that add up to 100 like this:

rand1 = 100-n3
rand2 = n3-n2
rand3 = n2-n1
rand4 = n1

How would I know which of these methods is more random?  And is there a better way?

---

### Post by Bachstelze on 2010-08-13
> **robots.jpg said:**
> Quick question for anyone with some comp-sci/math background:

I was comparing the results from the posted method and the first one I thought of, and the distribution of the results is very different.  For example, I'm much less likely to ever see "extreme" combinations like (97,1,1,1).  What I did was take three unique, random numbers between 1 and 99 (n1, n2, n3) sorted by value, and used them to generate the four numbers that add up to 100 like this:

rand1 = 100-n3
rand2 = n3-n2
rand3 = n2-n1
rand4 = n1

How would I know which of these methods is more random?  And is there a better way?

I think the second method is more random because with the first one, the final outcome may be determined after just one choice: if the first choice is 97, then the result is necessarily {97, 1, 1, 1}, which gives it a 1/97 probability, much larger than what you would expect with an ideal random selection*.

With the second one, the first choice can only determine one number: if the first choice is 1, since there is no smaller possible number, it has to be n1, so you know rand4 will be 1 (likewise if the first choice is 99, you know rand1 will be 1). There is no result with as high a probability as 1/97, so I believe it's much closer to an ideal random selection.

* An ideal random selection would be: determine all the possible results and pick one at random, there is obviously much more than 97 of them.

---

### Post by StephenF on 2010-08-13
The following Python code indicates the number of permutations that add up to 100. Just building the list takes considerable time and I imagine PHP would not be vastly different in speed.

```

>>> from itertools import *
>>> len(list(x for x in product(xrange(1, 98), xrange(1, 98), xrange(1, 98), xrange(1, 98)) if sum(x) == 100))
156849

```
I guess this rules out a table.

Edit:
Imagine a ribbon 100cm long that has marks at 1cm intervals that are authorized cutting points. This means there are 99 cutting points on the ribbon. Select three different places on the ribbon at random with no duplicate places so you have three places to cut, then the different ribbon lengths will be your numbers.

A choice of 99 in the first round leaves a length of 99 and 1. In the second round 99 is out but you can cut at three leaving a length of 3, 96, and 1. In the final round 3 and 99 are out. No further explanation necessary.

Edit2: Not PHP :-({|=
```
#! /usr/bin/env python

from random import sample
from itertools import izip

def slice_lengths(length=100, cuts=3):
    """Take a theoretical ribbon and slice it cuts number of times.
    
    The return value is a generator of the different lengths made.
    Parameters:
        length, a number greater than zero
        cuts, a number less than length
    """

    # Calculate where the positions of the ribbon edges will be.
    edge = [0] + sorted(sample(xrange(1, length), cuts)) + [length]
    
    # Deltas for a moving window of two values across edge.
    return ((b - a) for a, b in izip(edge, edge[1:]))
    
if __name__ == "__main__":
    s = tuple(slice_lengths())
    print s, "sum =", sum(s)
```
Sample output:
(13, 1, 32, 54) sum = 100

---

### Post by Hellkeepa on 2010-08-13
HELLo!

If you want a more uniform distribution, I would recommend using **Robot.jpg**'s method. Implemented here:
[php]
function robotRnd () {
	$Target = 100;
	$Num = array ();
	for ($Run = 0; $Run < 3; ++$Run) {
		do {
			$Tmp = mt_rand (1, 99);
		} while ($Num[$Tmp]);
		$Num[$Tmp] = $Run;
	}

	$Num = array_flip ($Num);
	sort ($Num);
	return array (100-$Num[2], $Num[2]-$Num[1], $Num[1]-$Num[0], $Num[0]);
}
[/php]

Happy codin'!

---

### Post by raf_kig on 2010-08-13
```

from random import shuffle, randint
def wo_shuffle(total=100, count=4):
    nums = []
    for i in range(count-1):
        x = randint(0,total)
        nums.append(x)
        total = total - x
    nums.append(total)
    shuffle(nums)
    return nums

```
There you go, we generate some random numbers that add up to 100 and then shuffle the result.
This gives a (perfectly, I assume) uniform distribution.

Regards,

raf_kig

---

### Post by Bachstelze on 2010-08-13
> **raf_kig said:**
> 
There you go, we generate some random numbers that add up to 100 and then shuffle the result.
This gives a (perfectly, I assume) uniform distribution.

Not quite. {97, 1, 1, 1} will still have a far higher probability than it would in an ideal random selection (> 1/(4*97)).

---

### Post by StephenF on 2010-08-13
```

from random import sample
from itertools import izip

def slice_lengths(length=100, cuts=3):
    edge = [0] + sorted(sample(xrange(1, length), cuts)) + [length]
    return ((b - a) for a, b in izip(edge, edge[1:]))
    
if __name__ == "__main__":
    three_ones_count = 0
    for i in range(1000000):
        for each in slice_lengths():
            if 1 < each < 97:
                break
        else:
            three_ones_count+= 1

    print "three ones occurrence %d / 1000000" % three_ones_count

```
If there are as previously calculated exactly 156849 permutations and there are 4 ways to make a number sequence with three ones in it out of a sample size of one million there should be an average 25.502234633 occurrences of that combination. This program is outputting between 20 and 30.

---

### Post by Ferrat on 2010-08-13
Well you could just make 4 random numbers from say 1-100

add those 4 up

and then work out what % of the total each number is

round them of if needed and check that the new total is 100, if not then add the difference to one of the numbers randomly

---

### Post by Npl on 2010-08-13
Lol, getting a uniform distribution is quite tricky in such a case. None of the attempt suffice so far and I doubt you have to do that if its some kinda homework.

I can give an attempt to explain it for the case of 3 values adding up to 100.
Each value is atleast 1 and at most 98 and unfortunately they are dependend, so you cant just generate them separately. Picture a triangle with 2 sides 97 units long and at 90 degree touching at (1,1) - X Axis beeing your first value, Y your second (and the third one cant be chosen but needs to be calculated). uniformly picking a point in the enclosed 2 dimensional area is what you need.
You cant fix one axis by uniformly picking a point on the side - if you for example randomly chose the X Coordinate then you have the same possibility for each vertical slice - that means **all** values (1,y,99-y) together (97 separate ones) have the same possibility as the single one (98,1,1). In other words (98,1,1) is 97 times more likely than (1,1,98 )

Instead you would need to generate a single number r between 1 and the total number of possibilities - (99*98 )/2. And then start running through all fields in the triangle. eg. (1,1), (1,2), ... (1,97), (2,1), (2,2),.., (2,96)(3,1).....
And stop at the r th field (after r-1 steps).

with 4 values its the same principle in 3 dimensions, only harder to run through all fields.

---

### Post by StephenF on 2010-08-13
> **Npl said:**
> None of the attempt suffice so far.So where is my code falling down? I'm getting predictable probabilities for the 97 and three 1's case.

Edit: 242 in ten million. Time to test for four 25s.
Edit: Only 66 in ten million, which is four times lower on account of there being only one permutation that can supply this.
Edit: Predicted 1530.134077999 for most combinations. Got 1524 on the first try searching for a combination of 1, 2, 3, 94 which has by my estimation 4! (that's factorial 4 = 24) permutations.

---

### Post by Npl on 2010-08-13
> **StephenF said:**
> So where is my code falling down? I'm getting predictable probabilities for the 97 and three 1's case.Try checking for explicit results and also not edge cases (in my example above (98,1,1) is the only result that has the right probability).

TBH, I dont know a thing about python, so I cant tell what izip and sample does... but if you take 3 random values you just cant get the right results

---

### Post by SoFl W on 2010-08-13
I haven't read through anyone else's code, but I would start with 100 and as I generated numbers subtract from 100, making the new random number the zero to the new number.


[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

---

### Post by trent.josephsen on 2010-08-13
Pretty sure StephenF has the right idea.  Keep in mind that it's not truly random no matter how you slice it (no pun intended); insisting that the numbers add to 100 eliminates the possibility of true randomness, but I am pretty sure his suggestion will get comparable distributions to the generate-all-and-pick-one algorithm.  Can't prove it, and my statistics is rusty, but it makes intuitive sense.

Ferrat's solution will also be pretty close to random, or so my instincts tell me.

---

### Post by StephenF on 2010-08-13
> **Npl said:**
> But if you take 3 random values you just cant get the right results.
If you have four numbers summing to 100 and imagine they to be lengths of pieces of string and place those pieces of string end to end to make a total length of 100 you would expect the places where they join to be at three random places would you not? Hence my three random numbers.

I'm aiming for a distribution matching a random selection of all possible permutations but insanely faster over the short haul since there is no table generation. Please let me know what your definition of right is.

The edge value of three ones and a 97 (in no particular order) predicted perfectly and the mid value with only one permutation for all 25's was four times less prevalent. Are you expecting a spike somewhere? If so do let on so I can test it.

---

### Post by Npl on 2010-08-13
> **StephenF said:**
> If you have four numbers summing to 100 and imagine they to be lengths of pieces of string and place those pieces of string end to end to make a total length of 100 you would expect the places where they join to be at three random places would you not? Hence my three random numbers.Thats a good point and a smart idea. Dint understood your approach the first time, i thought you`d fix one point after the other.
> **StephenF said:**
> I'm aiming for a distribution matching a random selection of all possible permutations but insanely faster over the short haul since there is no table generation. Please let me know what your definition of right is.Right would be an uniform distribution, and your program should be able to do that.

---

### Post by howlingmadhowie on 2010-08-14
Ferrat gave a good answer on the last page. something like this should do it:

```

n1=random()
n2=random()
n2=random()
n4=random()
weight=100/(n1+n2+n3+n4)
r1=round(n1*weight)
r2=round(n2*weight)
r3=round(n3*weight)
r4=round(n4*weight)
if(r1+r2+r3+r4 != 100) {
  /* some code to deal with possible rounding errors */
}

```

---

### Post by ssam on 2010-08-14
another method would be to generate 100 random numbers from 1-4. then count how many of each you have.

```

import random
numbers = [0,0,0,0]
for x in range(100):
  r = random.randint(0,3)
  numbers[r] += 1

print numbers
print sum(numbers)

```

each of the numbers will have a poisson distribution around 25.

i am not sure that you could have a uniform distribution of each of the numbers. there only a few permutations with a '97' in them (or a '100' if you allow [100,0,0,0]), where as there are many permutations with '25' in

[25,25,25,25]
[25,25,24,26]
[25,25,23,27]
...

---

