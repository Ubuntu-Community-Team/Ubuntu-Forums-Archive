---
title: "divide at random into 3"
date: 2011-01-31
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-31
I seem to have a mental block at the moment on this:

I have a quantity and I want to split into 3 such that all 3 parts add up to 100% of said quantity, also that each of those parts has equal probability but that their proportion of the whole is still randomly chosen.

The best I can come up with at the moment is:
[php]
	unsigned int aPart[3];
	aPart[0] = aPart[1] = aPart[2] = 0; // clear the counters
	for (int i = 0; i < iQuantity; ++i) aPart[rand()%3]++; // distribute at random
[/php]

However that soon takes ages when doing a lot of them with largish quantities... there has to be a better way :confused:

---

### Post by Ferrat on 2011-01-31
a bit of sudo code but 

init part1=0, part2=0, part3=0;
init totaltSum = whatever input
init tempSum = totalSum;

part1 = (random <= tempSum);
tempSum = tempSum - part1;

part2 = (random <= tempSum);
tempSum = tempSum - part2;

part3 = tempSum;
tempSum = tempSum - part3;

check>
if ((part1+part2+part3) != totalSum)
     error...
else
    yay!

---

### Post by MadCow108 on 2011-01-31
as you need them to add up to 100% you only need two random variables:
```

r1 = rand()%iQuantity
r2 = rand()%iQuantity
if (r1 > r2)
  swap(r1, r2)
a[0] = r1
a[1] = r2 - r1
a[2] = iQuantity - r2

```

---

### Post by squenson on 2011-01-31
Interesting mathematical problem. It seems that the two approaches (randomly allocating each element in one of the three groups; or cutting the total quantity in 3 using 2 random variables) will return different probabilities of the distribution that can be obtained.

For example, if you have 20 elements, the probability that no element is allocated to group 1 is: (2/3)^20 = 0.0003 while if you use the variables r1 and r2, the probability that r1 = 0 or r2 = 0 is 0.0975.

---

### Post by worksofcraft on 2011-01-31
> **Ferrat said:**
> a bit of sudo code but 

init part1=0, part2=0, part3=0;
init totaltSum = whatever input
init tempSum = totalSum;

part1 = (random <= tempSum);
tempSum = tempSum - part1;

part2 = (random <= tempSum);
tempSum = tempSum - part2;

part3 = tempSum;
tempSum = tempSum - part3;

check>
if ((part1+part2+part3) != totalSum)
     error...
else
    yay!

Thanks :)

This is roughly what I tried to start with but then I discovered as follows:

On average I get part 1 has 50% of the total,
Part 2 and 3 only have 25% each :(

p.s. I'm just doing a histogram of madcow's method to see what happens there :)

update: no... there a[1] is on average about 25% bigger than the other two :confused:
see what I mean about "mental block" :shock:

---

### Post by Ferrat on 2011-01-31
> **worksofcraft said:**
> Thanks :)

This is roughly what I tried to start with but then I discovered as follows:

On average I get part 1 has 50% of the total,
Part 2 and 3 only have 25% each :(

p.s. I'm just doing a histogram of madcow's method to see what happens there :)

Yeah that could be a problem, you could try and then do a random function for what number ends up in what part, that would help the problem somewhat, in theory it should be just as likely to get 0 or max as any other number but random with computers is often tricky.

---

### Post by cyberslayer on 2011-02-01
> **worksofcraft said:**
> p.s. I'm just doing a histogram of madcow's method to see what happens there :)

update: no... there a[1] is on average about 25% bigger than the other two 

Yeah, the problem is that his code makes the first value tend to be larger than the other two since it is the max of the first two values.  You could randomly permute the order but I think that the three random values will still have different distributions since subtracting the second random number from the first will tend to make one of the values much larger compared to the others.

Here is a method that I think will work:

Let X_1, X_2 and X_3 be three uniformly independent random variables in the interval [0, 1].  Define Y_i = X_i / |X_1 + X_2 + X_3| for i = 1, ..., 3.  Note that dividing by zero here is not an issue since the variables are continuous so the probability any of them is 0 (or all of them are 0 for that matter) is 0; of course, if you implement this you will have to do something to prevent division by 0 since then your variables will be discrete so the probability of dividing by zero will no longer be 0.  Clearly, the values Y_i are identically distributed and sum to 1.  It follows that E[Y_i] = 1/3.

---

### Post by Vaphell on 2011-02-01
i don't think madcow's approach is valid, given the assumption that *each of those parts has equal probability but that their proportion of the whole is still randomly chosen*
when you slice the range according to some random numbers that sum up to 100% you effectively assign those numbers as probabilities to subsets, thus the whole exercise fails the 'equal probability' clause.

If i had to cheat I'd try something like S(P[i]) + D(N) = 100%
D acts as an imperfection of the system, remaining part of 100% is perfectly split between players. I think that D should be a function of N, more samples = better accuracy, so e^(-N) maybe? (N=inf. -> D=0 -> perfect probabilities) That D would be split randomly among the subsets so the influence of randomness on total distribution is much smaller.

---

### Post by worksofcraft on 2011-02-01
> **Vaphell said:**
> ...
If i had to cheat I'd try something like S(P[i]) + D(N) = 100%
D acts as an imperfection of the system, remaining part of 100% is perfectly split between players. I think that D should be a function of N, more samples = better accuracy, so e^(-N) maybe? (N=inf. -> D=0 -> perfect probabilities) That D would be split randomly among the subsets so the influence of randomness on total distribution is much smaller.

I thought I understood that until I tried to code it and realized I really didn't know what I was trying to code :shock: However thinking of it as a random distribution of cards amongst 3 players does help clarify the problem :)

So anyway I did try cyberslayer's method and that seems to work nicely :)

To avoid calculating 0/0 (or something inaccurately close to that) I put in a minimum threshold for the total sum. Drawing again if it was too low. I'm not completely sure that this doesn't slightly  bias the system to get less low numbers, but the statistical averages seem good and distributions doesn't appear to favor any particular value (see attached image).

Thank's, that is a lot faster than picking which pile to add each and every card to at random :)

---

### Post by cyberslayer on 2011-02-01
> **worksofcraft said:**
> So anyway I did try cyberslayer's method and that seems to work nicely :)

To avoid calculating 0/0 (or something inaccurately close to that) I put in a minimum threshold for the total sum. Drawing again if it was too low. I'm not completely sure that this doesn't slightly  bias the system to get less low numbers, but the statistical averages seem good and distributions doesn't appear to favor any particular value (see attached image).

Thank's, that is a lot faster than picking which pile to add each and every card to at random :)

This seems like a decent method to avoid division by 0.  It could introduce a very small amount of skew towards larger numbers but it depends what range of integers you are sampling from, what specific value the cutoff was and other implementation issues.  If such small amounts of skew are a problem, you could fix it by choosing the right cutoff value and sampling from the right range of integers.

---

### Post by nvteighen on 2011-02-01
I don't get your problem :P If it's just sectioning a number into three random segments with equal probability, then, all you need is to specify two random numbers between a range and make sure the second number is higher than the first. Those are the **lengths** of your segments... then, substract the sum of the random ones to create the third one...

```

import random

def random_trisection(num, generator = random.random):
    """The generator argument be any random generator you like, as long as it
    returns something in the range [0, 1] and takes no argument. It uses
    Python's standard random.random by default."""
    
    first_cut = num * generator()
    second_cut = (num - first_cut) * generator()

    return (first_cut, second_cut, num - (second_cut + first_cut))


```

This is a test sample:
```

>>> segments = random_trisection(10)
>>> segments
(3.9926770587462257, 2.5240573911518682, 3.4832655501019065)
>>> reduce(lambda x, y: x + y, segments) # Sum everything up
10.0
>>> 

```

But it's very probable that I misunderstood the problem.

---

### Post by Arndt on 2011-02-01
> **nvteighen said:**
> I don't get your problem :P If it's just sectioning a number into three random segments with equal probability, then, all you need is to specify two random numbers between a range and make sure the second number is higher than the first. Those are the **lengths** of your segments... then, substract the sum of the random ones to create the third one...

```

import random

def random_trisection(num, generator = random.random):
    """The generator argument be any random generator you like, as long as it
    returns something in the range [0, 1] and takes no argument. It uses
    Python's standard random.random by default."""
    
    first_cut = num * generator()
    second_cut = (num - first_cut) * generator()

    return (first_cut, second_cut, num - (second_cut + first_cut))


```

This is a test sample:
```

>>> segments = random_trisection(10)
>>> segments
(3.9926770587462257, 2.5240573911518682, 3.4832655501019065)
>>> reduce(lambda x, y: x + y, segments) # Sum everything up
10.0
>>> 

```

But it's very probable that I misunderstood the problem.

But your first segment will be num/2 on average, and the other two will be num/4.

---

### Post by Arndt on 2011-02-01
> **worksofcraft said:**
> I thought I understood that until I tried to code it and realized I really didn't know what I was trying to code :shock: However thinking of it as a random distribution of cards amongst 3 players does help clarify the problem :)

So anyway I did try cyberslayer's method and that seems to work nicely :)

[...]

Thank's, that is a lot faster than picking which pile to add each and every card to at random :)

I know you marked it solved, but I think what you ended up with is not equivalent to your original discrete partitioning code. That one is, loosely spoken, very likely to make the three heaps about equal in size, while the uniform distributions which you add in the other method will make the smallest heap very small with a relatively large probability.

If the card distribution model is what you want, you need to find out the probability distribution for the size of one heap, and then use that distribution in the addition method, instead of a uniform one.

The average size of the smallest segment ought for example to be quite different.

---

### Post by Arndt on 2011-02-01
> **Arndt said:**
> 
If the card distribution model is what you want, you need to find out the probability distribution for the size of one heap, and then use that distribution in the addition method, instead of a uniform one.


On further thought, it's not obvious that doing this gives the same result, since then we are adding three independent variables, while they are interdependent in the first case.

---

### Post by Lux Perpetua on 2011-02-01
Your wording of the question really isn't clear, but I think you want a triple (x, y, z) that is uniformly distributed over the set of (x, y, z) such that x, y, z are nonnegative and x + y + z = 1. If that is indeed what you want, then you can use the following method: 

- Generate two random numbers x, y in the range [0, 1].
- Let z = 1-(x+y). If z < 0, then set (x, y, z) = (1-x, 1-y, -z).

That gives you a uniform distribution. Why: your problem is exactly the same as generating a uniformly random point inside a triangle. You can do this by generating a point inside a parallelogram (here, a square) and using the fact that the parallelogram is made of two triangles. 

However, your original solution, which takes N items and randomly assigns each to one of three bins, does not generate anything close to a uniform distribution, but rather a **multinomial** distribution, which is biased toward roughly equal bin sizes.

---

### Post by worksofcraft on 2011-02-01
> **Lux Perpetua said:**
> Your wording of the question really isn't clear, but I think you want a triple (x, y, z) that is uniformly distributed over the set of (x, y, z) such that x, y, z are nonnegative and x + y + z = 1. If that is indeed what you want, then you can use the following method: 

- Generate two random numbers x, y in the range [0, 1].
- Let z = 1-(x+y). If z < 0, then set (x, y, z) = (1-x, 1-y, -z).

That gives you a uniform distribution. Why: your problem is exactly the same as generating a uniformly random point inside a triangle. You can do this by generating a point inside a parallelogram (here, a square) and using the fact that the parallelogram is made of two triangles. 

However, your original solution, which takes N items and randomly assigns each to one of three bins, does not generate anything close to a uniform distribution, but rather a **multinomial** distribution, which is biased toward roughly equal bin sizes.

yes... awesome, that is **exactly** what I wanted :)
Also thanks for showing how valuable it is to state the problem in unambiguous mathematical terms.

As you say, the distribution of each card at random did have an overall sort of averaging effect on the bin sizes. Once I had played with it for a bit I realized that wasn't really what I wanted... as well as being very slow.


p.s. in particular that geometrical image of that uniformly placed point inside a square with the dividing diagonal line of x+y = 1. In attached image I scaled it up by 256 so I can do an integers scatter plot.

---

### Post by StephenF on 2011-02-01
Déjà vu. (accents courtesy of Wikipedia copy and paste.)

[http://ubuntuforums.org/showthread.php?t=1552079](http://ubuntuforums.org/showthread.php?t=1552079)

---

### Post by worksofcraft on 2011-02-01
> **StephenF said:**
> Déjà vu. (accents courtesy of Wikipedia copy and paste.)

[http://ubuntuforums.org/showthread.php?t=1552079](http://ubuntuforums.org/showthread.php?t=1552079)

Not really. Lux Perpetua's solution would not work for dividing it into 4 random piles with equal distribution and presumably those solutions don't work for dividing it in 3.

I do now wonder if there is a generic solution for dividing it in N... although I don't need that at the moment.

p.s. On Ubuntu you can use character map for accents. It is under Applications->Accessories->Character Map

---

### Post by StephenF on 2011-02-01
```

from random import sample
from itertools import izip

def slice_lengths(length=100, cuts=3):
    edge = [0] + sorted(sample(xrange(1, length), cuts)) + [length]
    return ((b - a) for a, b in izip(edge, edge[1:]))

```
As good as generating all possible combinations and picking one at random IMHO. As you can see you may specify any number of cuts (within reason) giving cuts+1 lengths.

---

### Post by Vaphell on 2011-02-02
it appears i totally misunderstood the problem and overcomplicated a little, damn it :)
i thought it's about a believable distribution where the odds of subsets are equal because that is what the modulo arithmetic with N tries indicated.
There is a difference between cutting a cake to 3 random pieces and spinning an evenly cut cake, dropping N cherries on it and then counting where they landed. Oh well...

---

### Post by Arndt on 2011-02-03
Sorry for beating the dead horse once more, but I have three more observations:

1) Generating three numbers X, Y and Z and then using X/(X+Y+Z) etc. does not yield the same distribution as Lux Perpetua's solution (my empirical studies only) - the numbers are more concentrated towards the middle.

2) It's very easy to introduce bias without meaning to, if the method isn't obviously symmetric. I tried a method which could be said to generate three points on a circle, and then calculating the arc distances, but when I didn't shuffle them afterwards, the discontinuity at 0/1 caused one of the numbers to be larger on average. It took me some time to realize why.

3) So, if the distribution actually matters, test the algorithm in isolation until you're satisfied with it.

---

### Post by worksofcraft on 2011-02-03
> **Arndt said:**
> Sorry for beating the dead horse once more, but I have three more observations:

1) Generating three numbers X, Y and Z and then using X/(X+Y+Z) etc. does not yield the same distribution as Lux Perpetua's solution (my empirical studies only) - the numbers are more concentrated towards the middle.

2) It's very easy to introduce bias without meaning to, if the method isn't obviously symmetric. I tried a method which could be said to generate three points on a circle, and then calculating the arc distances, but when I didn't shuffle them afterwards, the discontinuity at 0/1 caused one of the numbers to be larger on average. It took me some time to realize why.

3) So, if the distribution actually matters, test the algorithm in isolation until you're satisfied with it.

Yes I agree, working with random numbers it is very easy to miss how subtle changes can produce a completely different result. Quite often I just have to go with something seems about right and make a mental note that it should be analysed properly at some stage.

> **Vaphell said:**
> it appears i totally misunderstood the problem and overcomplicated a little, damn it :)
i thought it's about a believable distribution where the odds of subsets are equal because that is what the modulo arithmetic with N tries indicated.
There is a difference between cutting a cake to 3 random pieces and spinning an evenly cut cake, dropping N cherries on it and then counting where they landed. Oh well...

Indeed and would you believe... I didn't even realize that cutting a cake into 3 equal pieces and then randomly scattering cherries on them would produce a different result to evenly distributing cherries and then cutting that cake into 3 random pieces :shock:

I really liked your idea of "cheating" by using the desired distribution function directly... but then I couldn't work out how to convert linear distributed random numbers from rand function to said distribution :confused:

It really would mean spending a couple of days refreshing my statistics maths to get my mind sent back on track with that.

---

### Post by Lux Perpetua on 2011-02-03
> **Arndt said:**
> Sorry for beating the dead horse once more, but I have three more observations:

1) Generating three numbers X, Y and Z and then using X/(X+Y+Z) etc. does not yield the same distribution as Lux Perpetua's solution (my empirical studies only) - the numbers are more concentrated towards the middle.

2) It's very easy to introduce bias without meaning to, if the method isn't obviously symmetric. I tried a method which could be said to generate three points on a circle, and then calculating the arc distances, but when I didn't shuffle them afterwards, the discontinuity at 0/1 caused one of the numbers to be larger on average. It took me some time to realize why.

3) So, if the distribution actually matters, test the algorithm in isolation until you're satisfied with it.You're right, (X, Y, Z)/(X+Y+Z) isn't uniformly distributed. I think mine and StephenF's (morally) are the only solutions in this thread that generate a uniform distribution. 

I started typing up an intuitive geometrical explanation of why the (X, Y, Z)/(X+Y+Z) distribution can't be uniform, but it started getting pretty involved, so I'll skip the details and just give a sketch. It's equivalent to generating a point in the unit 3-dimensional cube ([0,1]x[0,1]x[0,1]), drawing a line through the origin and your point, and returning the coordinates of the intersection of this line and the equilateral triangle with vertices {(1,0,0), (0,1,0), (0,0,1)}. The resulting distribution being nonuniform just means the probability of hitting a region on the triangle is not exactly proportional to its area. To see this, you can consider a tiny region on the triangle and its preimage in the cube and argue that the ratio of the volume of the preimage to the area of the region on the triangle is not constant. It's not a difficult argument, but it's a little tricky for me to explain without visual aids, so I'll just leave you to think about it. 

> **worksofcraft said:**
> Not really. Lux Perpetua's solution would not work for dividing it into 4 random piles with equal distribution and presumably those solutions don't work for dividing it in 3.

I do now wonder if there is a generic solution for dividing it in N... although I don't need that at the moment.

p.s. On Ubuntu you can use character map for accents. It is under Applications->Accessories->Character Map
My solution is for n=3, but the geometric idea does generalize. One realization is basically StephenF's solution: 

> **StephenF said:**
> ```

from random import sample
from itertools import izip

def slice_lengths(length=100, cuts=3):
    edge = [0] + sorted(sample(xrange(1, length), cuts)) + [length]
    return ((b - a) for a, b in izip(edge, edge[1:]))

```
As good as generating all possible combinations and picking one at random IMHO. As you can see you may specify any number of cuts (within reason) giving cuts+1 lengths.

...well, without the "generate all possible solutions first" part, which I don't really understand. Here's the abstract algorithm: 

- Generate n-1 random numbers u[1], u[2], ..., u[n-1] in the range [0,1]. 
- Sort u[1:n]. Let u[0] = 0 and u[n] = 1. 
- Let x[i] = u[i+1] - u[i] for i = 0, ..., n-1. 

At the end, x[0:n] is uniformly distributed over the set of nonnegative x[0], ..., x[n-1] satisfying x[0] + ... + x[n-1] = 1. It's not too hard to see that this distribution is uniform: we're trying to generate a random point inside the standard (n-1)-dimensional simplex. The algorithm uses the fact that the (n-1)-dimensional unit cube can be decomposed into (n-1)! congruent simplices: one simplex has vertices {(0,...,0), (0,...,0,1), ..., (0,1,...,1), (1,...,1)}, and you get all the other simplices by permuting the coordinates. Now it's just a matter of generating a random point inside the unit cube, folding all of the (n-1)! simplices onto the one defined above (i. e., sorting the coordinates), and transforming this simplex to the "standard" (n-1)-dimensional simplex with vertices {(1,0,...,0), (0,1,0,...,0), ..., (0,...,0,1)}. 

> **worksofcraft said:**
> p.s. in particular that geometrical image of that uniformly placed point inside a square with the dividing diagonal line of x+y = 1. In attached image I scaled it up by 256 so I can do an integers scatter plot.Nice plot. :-) Unfortunately, it's harder to make useful plots for n > 3, but it should be possible with some creativity (taking thickened 2-dimensional slices or something).

---

