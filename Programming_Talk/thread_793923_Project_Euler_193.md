---
title: "Project Euler 193"
date: 2008-05-14
forum: Programming Talk
---

### Post by Lster on 2008-05-14
Hi there!

Project Euler 193 has been puzzling me for a while now. I haven't been making progress so I was wondering if anyone had an idea how to do it? For reference, [http://projecteuler.net/index.php?section=problems&id=193](http://projecteuler.net/index.php?section=problems&id=193).

The problem states that we need to find the number of integers less than 2^50 that do not have any repeated prime factors. So similarly we could find the number of integers less than 2^50 and divisible by 4, 9, 25, 49... and subtract that from 2^50-1.

So I thought about doing floor(2^50 / 4) + floor(2^50 / 9) + floor(2^50 / 25) + floor(2^50 / 49) etc... but of course there would be some overlap. I cannot see how to create an algorithm that accounts for overlap but maybe there is a way? There are 2063689 numbers that would need to have this done for (all the prime numbers squared that are less than 2^50), so it would have to be a pretty fast algorithm! :p

Perhaps there is another way?

Thank you,
Lster

---

### Post by happyhamster on 2008-05-14
Why would there be overlap?

---

### Post by Lster on 2008-05-14
Consider finding every number that is either a multiple of 2 or 3, less than or equal to 10.

1 in 2 numbers are divisible by 2 so you can work out that there are 10/2 = 5 numbers less than or equal to 10 and that have a factor of 2. Similarly there are 10/3 = 3 numbers divisible by 3, less than or equal to 10.

So if we go back to are original question. Are there 5+3 = 8 numbers less than or equal to 10 that contain 2 or 3 as a factor? No! :)

That's because the group of number that contain multiples of 2 is:

2, 4, 6, 8, 10

Similarly, the multiples of 3 are:

3, 6, 9

Note that we have 6 repeated twice! We have counted the number 6 in both sets. To remove it we can simply subtract 10/6 = 1, giving us the correct answer 5+3-1=7.

Here they are:

2, 3, 4, 6, 8, 9, 10

:)

---

### Post by nvteighen on 2008-05-14
> **Lster said:**
> (...)
Note that we have 6 repeated twice! We have counted the number 6 in both sets. To remove it we can simply subtract 10/6 = 1, giving us the correct answer 5+3-1=7.

Here they are:

2, 3, 4, 6, 8, 9, 10

:)

Pardon me, but that removing is logically acceptable only if you know where overlapping occurs. [EDIT]Ha, ha... That is what you actually want to solve. Excuse me![/EDIT]

Doesn't it occurs when you get two or more of the seeked prime factors multiplied? Note the (amazing... ;)) fact that 6=2*3. For any given number you try to factorize in a and b, if n = a * b is a product, it will appear in both series.

So, could this be reduced to a combinatorial maths problem?

---

### Post by happyhamster on 2008-05-14
Ah, ok, thanks. I manually tested the first 32 numbers. But I now see the first problem would arise at 36 (4x9). Which explains why I thought it would work out-of-the-box-without-any-silly-overlapping-heh.

My math is too rusty I guess :)

---

### Post by Lster on 2008-05-14
nvteighen, I'm not quite sure I follow it entirely. The main issue here, though, is that I can't evaluate whether a number is squarefree on a per-integer basis - 2^50 is just too large.

There are plenty of ways of doing this, but none are fast enough. For example, you could find all the primes up to squareroot of 2^50 and square them. Also find all the prime numbers up to (and including) 2^50/4. Then you just have to find the number of ways you can multiply a prime squared by any number of primes and it equals less than n.

For example, for less than 14:

Square primes:
[INDENT]4, 9[/INDENT]
Primes less than or equal to 14/4 = 3:
[INDENT]2, 3[/INDENT]

4, 4*2, 4*3
9

14-1-4 = 9. So there are 9 numbers under 14 that are squarefree! :)

---

### Post by happyhamster on 2008-05-14
Ok, how about this: you already know there are n=2063689 (how on earth did you find that out?) prime-squareds below 2^50. Then the possible multiplications between them are*:

n!/(n-2)! = n*(n-1)

Only half of those give a unique result, so the number is n*(n-1)/2. Next problem is that some of those multiplications will be larger than 2^50.

So, a possible solution would be to brute-force determine which products are too large, counting down from n.

Does this make any sense?

* I had to go to wikipedia to digg that one up of course.
[http://en.wikipedia.org/wiki/Permutation](http://en.wikipedia.org/wiki/Permutation)

---

### Post by Lster on 2008-05-14
I found the number 2063689 by simply finding the next prime number until it was greater than sqrt(n). But I don't think that way would work. It *would* give the number of ways you could multiply any two elements in this list, but that isn't quite what we want to find.

We want to find the number of ways each one of these can be multiplied by a number of primes and still be less than 2^50.

Your method would never count, for example, the value 8 as having a prime factor twice. Maybe I'm misunderstanding?

---

### Post by happyhamster on 2008-05-14
> **Lster said:**
> Maybe I'm misunderstanding?
Nope. This is tough :)

---

### Post by Lster on 2008-05-14
I can see so many algorithms and chances, but none are fast enough. This *is* really hard! :)

---

### Post by Lux Perpetua on 2008-05-14
I haven't tested this, so I'm not sure this will be fast enough. (**Warning: possible spoilers below.**) 

Since none of what I'm about to say depends on the precise value of 2^50, let 2^50 = N, and we'll try to describe a method to find the number of squarefree positive integers less than a general N. Let's start by iterating over the primes and seeing how many multiples their squares have. 

The first prime is 2, whose square is 4. There are floor(N/4) multiples of 4.

The second prime is 3, whose square is 9. There are floor(N/4) multiples of 9. Now we're up to floor(N/4) + floor(N/9)...but wait. What about multiples of 4*9 = 36? Those are both multiples of 4 *and* multiples of 9, so we're counting them twice! We will rectify this by subtracting the number of multiples of 36, namely floor(N/36). So now we're up to floor(N/4) + floor(N/9) - floor(N/36). This way, the multiples of 36 get counted only once.

The third prime is 5, whose square is 25. There are floor(N/25) multiples of 25. Now we're up to floor(N/4) + floor(N/9) + floor(N/25) - floor(N/36)...but wait. What about multiples of 4*25 = 100 and 9*25 = 225? Just as above, we're counting those twice, so we need to subtract the number of multiples of 100 and of 225. This brings us to

floor(N/4) + floor(N/9) + floor(N/25) - floor(N/36) - floor(N/100) - floor(N/225)...

...but hang on. What about multiples of 4*9*25 = 900? Those are multiples of *all* of 4, 9, 25, 36, 100, and 225. Let's see how many times we're counting those. For 4, 9, and 25, they get counted once, so we're up to 3. For 36, 100, and 225, they get counted once, but we're subtracting those terms, so the multiples of 900 in total are counted 3 - 3 = 0 times. So wee need to add floor(N/900) to count the multiples of 900. This finally brings us to 

floor(N/4) + floor(N/9) + floor(N/25) - floor(N/36) - floor(N/100) - floor(N/225) + floor(N/900).

Et cetera. 

I said at the beginning that I wasn't sure it would be fast enough. At first it would seem to have no hope of working, since N = 2^50 is so huge. However, the *square root* of 2^50 is what really counts, and that's only 2^25 = 33,554,432.

---

### Post by Lster on 2008-05-14
I also went somewhat that way but not nearly that far! So what would be the next expansions be? Is there definitely a pattern there? It seems like:

[LIST=1]
[*]a
[*]a + b - ab
[*]a + b + c - ab - ac - bc + abc
[*]a + b + c + d - ab - ac - ad - bc - bd - cd + abc + abd + acd + bcd - abcd
[/LIST]

Is this right?

---

### Post by nanotube on 2008-05-14
so, the total number of integer divisions you'd need for 2^50, using your algorithm (which seems logically sound to me) is 
sum(i from 1 to 2063689) = 2129407176205

(when you move on to the next prime, you must do a division by that prime's square, plus a division by the product pairs of this prime's square and the square of all preceding primes)

on my machine, python takes 0.5 secs to do 1 million integer divisions of 2^50. 

```
>>> t = timeit.Timer(stmt="1125899906842624L/25")
>>> t.timeit()
0.53455901145935059
```

so, the total time to execute this algorithm would be, roughly, 12.3 days. 

```
>>> 2129407 * 0.5 / 3600/24
12.322957175925927

```

we must add some overhead for looping over a list of primes, adding and subtracting the results of each division to a total (a million additions or subtractions take 0.15 secs or so on my machine, so that's another 4 days right there), finding the products of all pairs of prime-squares, etc. so let's maybe double it to be on the safe side, roughly.

not bad - pretty doable. probably would be about an order of magnitude or two faster if implemented directly in c, too, so even more doable. and the problem is also eminently parallelizable, so it's possible to farm out a portion of the work to multiple processors.

leaves me wondering if there isn't an even more efficient solution, though... :)

edit: see lster's post above and my post below - there are actually more calculations than that, so the numbers get a lot hairier than this...

---

### Post by nanotube on 2008-05-14
> **Lster said:**
> I also went somewhat that way but not nearly that far! So what would be the next expansions be? Is there definitely a pattern there? It seems like:

[LIST=1]
[*]a
[*]a + b - ab
[*]a + b + c - ab - ac - bc + abc
[*]a + b + c + d - ab - ac - ad - bc - bd - cd + abc + abd + acd + bcd - abcd
[/LIST]

Is this right?

no, you don't need the higher-order terms, only second-order pairs. think about it - the pairs already catch all the duplicates, third order terms would multi-count the duplicates. 

since these are primes, there are no intersections between factors of ab and factors of ac. so you don't need the abc to "add back" any factors you accidentally double-subtracted, because there are none.

unless my thinking is off here? :)

edit: never mind, my thinking /is/ off, you were right. :)

---

### Post by Lster on 2008-05-14
I'm not entirely sure of that myself. I can't see it for higher levels than three! :)

---

### Post by Lux Perpetua on 2008-05-14
> **nanotube said:**
> so, the total number of integer divisions you'd need for 2^50, using your algorithm (which seems logically sound to me) is 
sum(i from 1 to 2063689) = 2129407176205

(when you move on to the next prime, you must do a division by that prime's square, plus a division by the product pairs of this prime's square and the square of all preceding primes)

on my machine, python takes 0.5 secs to do 1 million integer divisions of 2^50. 

```
>>> t = timeit.Timer(stmt="1125899906842624L/25")
>>> t.timeit()
0.53455901145935059
```

so, the total time to execute this algorithm would be, roughly, 12.3 days. 

```
>>> 2129407 * 0.5 / 3600/24
12.322957175925927

```

we must add some overhead for looping over a list of primes, adding and subtracting the results of each division to a total (a million additions or subtractions take 0.15 secs or so on my machine, so that's another 4 days right there), finding the products of all pairs of prime-squares, etc. so let's maybe double it to be on the safe side, roughly.

Actually, you don't need to do so many divisions, because you only need to consider products of distinct primes (again, squarefree numbers) whose squares are less than 2^50. I estimate the number of those as about 20.4 million, which is not bad at all. More concerning to me is the fact that you need to *know* those 20.4 million squarefree numbers and the number of prime factors they have (this becomes clear when you generalize the pattern of the plusses and minuses in the summation). That's the only reason it might not be feasible.

---

### Post by Lster on 2008-05-14
There are 2063689 primes less than 2^25. Calculating them is quite quick - about 30 seconds on my computer. I'm still not sure about the pattern of intersections though...

---

### Post by Bichromat on 2008-05-14
> **Lster said:**
> There are 2063689 primes less than 2^25. Calculating them is quite quick - about 30 seconds on my computer. I'm still not sure about the pattern of intersections though...

Did you code the generator yourself ? In what language ? The basic algorithm in python is way too slow... :(
Not that it is a surprise...

What I find strange with this problem is that it takes a lot of time. It does not fit with the philosophy of Project Euler.

To find the intersections, you need to remove combinations of 2 primes (with no repetitions), that's 2063689!/(2!*(2063689-2)!) combinations, then all the  combinations involving 3 primes: 2063689!/(3!*(2063689-3)!) etc.

That's a HUGE number of combinations to try. Part of these combinations will be larger than 2^50, but I don't know if there's an easy way to find which ones, apart from testing them all.

EDIT : Big mistake, we are looking for combinations of squares of primes, not primes. Plus, we do not have to check a large number of combinations, because (2*3*5*7*11*13*17*67)^2 is already greater than 2^50.

---

### Post by Lster on 2008-05-14
Wouldn't that take... literally ages!? ;)

There has got to be a good way of doing this!

EDIT: By the way, I used C to calculate the primes. :)

---

### Post by happyhamster on 2008-05-14
Crap, I can't even get my program to calculate the number of primes. I get a segmentation fault each time (presumably because the arrays are too big). 

I'm currently teaching myself C, using a brand new copy of K&R. Am almost done with chapter 3 now, so it's probably better if I revisit this thread when I'm finished. See you in half a year or so :lolflag:

---

### Post by Bichromat on 2008-05-14
Actually, finding the combinations of squares is equivalent to finding the square-free numbers: a combination of non-repeating squares is the square of a combination of non-repeating primes ie the square of a square-free number:

4*9=(2*3)^2=6^2
4*9*25=(2*3*5)^2=30^2
etc.

So the "floor and intersection" method is more inefficient than finding the square-free numbers directly...

I have realized that we need to check the combinations of every two primes under 2^(50/2) (because no product must be greater than 2^50), then the combinations of every three primes under 2^(50/3) (for the same reason), then ... 4 ... under 2^(50/4) etc.
The good news is that these numbers decrease rapidly and you should be able to calculate that !

---

### Post by Lux Perpetua on 2008-05-14
> **Bichromat said:**
> So the "floor and intersection" method is more inefficient than finding the square-free numbers directly...No, since with the division method, we only need to find the squarefree numbers up to sqrt(N). If N is 2^50, then sqrt(N) = 2^25, and there are only in the ballpark of 20.4 million squarefree numbers less than 2^25. How I got 20.4 million: asymptotically, for large N, the fraction of the numbers less than N that are squarefree approaches 6/pi^2*****, and 2^25*6/pi^2 is about 20.4 million. On the other hand, 2^50*6/pi^2 is more than 684 trillion. On current hardware, 20.4 million is a feasible number of objects to consider, whereas 684 trillion is not. 

Also, the method you suggest wouldn't work, since for example the product of 2 numbers can be less than 2^50 even if one of them is greater than 2^25 (as long as the other one is smaller).

***** For emphasis, the squarefree/total = 6/pi^2 ratio is an *asymptotic* formula: as N grows to infinity, the ratio approaches 6/pi^2. It isn't exactly 6/pi^2 for finite N (can't be, since 6/pi^2 is irrational).

---

### Post by Bichromat on 2008-05-15
Yep, I just found out this morning that I was wrong in the computation of my combinations (that's what I get for staying up too late). For example, with combinations of 2 primes, we don't know that the two will be less than 2**25. We only know that the smallest will be. Then, the largest will be under 2**50/smallest.

So, the number of square-free with two prime factors will be :
sum(for i in Np(1,2**25)) [Np(i,2**50/i)]

where Np(a,b) is the number of primes between a and b.

---

### Post by Lster on 2008-05-15
Wouldn't that method require every prime number up to 2^50? Calculating more than all the primes less than 2^25 isn't really feasible.

---

### Post by Bichromat on 2008-05-15
> **Lster said:**
> Wouldn't that method require every prime number up to 2^50? Calculating more than all the primes less than 2^25 isn't really feasible.
Yup, it's horrible. To try Lux Perpetua's idea, see if you can generate all the square-free under 2**25. To do this, start with a list of the first square-free number, then multiply the list by a prime and append, recursively :

[1]*2=[2]
[1,2]*3=[3,6]
[1,2,3,6]*5=[5,10,15,30] etc.

Of course, only add a number to the list if it's smaller than 2**25. (There may be a smarter way to do this than just multiplying and comparing)

Edited part :
Once you have this list, square the numbers. They are the denominators of the "intersection terms" floor(N/(4*9)) etc.

---

### Post by Lster on 2008-05-15
Would that work?

Wouldn't you miss out numbers such as 2*3*5*7*11*13*17*23*29*29 = 9874794930, as its square root is irrational?

---

### Post by Lster on 2008-05-15
OK here is a quick Python script that does just that! I think 2^25 will take too long in Python though (I make it in the region of 16777216 array elements!).

[PHP]
primes = [ 2 ]

def isprime ( x ):
	s = int ( x ** 0.5 )
	i = 0
	while primes [ i ] <= s:
		if x % primes [ i ] == 0:
			return False
		
		i += 1
	
	return True

def genprimes ( ):
	global primes
	for i in xrange ( 3 , 2 ** 5 ):
		if isprime ( i ):
			primes += [ i ]

genprimes ( )
print "Primes initialized!"

sf = [ 1 ]

i = 0
while i < len ( primes ):
	n = sf [ :: ]
	for j in n:
		if j * primes [ i ] < 2 ** 5:
			sf += [ j * primes [ i ] ]
	
	i += 1

sf . sort ( )
print sf

[/PHP]

---

### Post by Bichromat on 2008-05-15
I edited my previous message. There is actually no need to do combinations, because we replaced combinations (products) of squares of primes by squares of square-less numbers. Okay... I think I got it right this time. I can hear my brain melting...

---

### Post by Lster on 2008-05-15
I agree now... Good thinking! :)

I'll implement that when I get home from my Physics Practical. Don't you hate exams? ;)

---

### Post by Bichromat on 2008-05-15
> **Lster said:**
> I agree now... Good thinking! :)

Oh, wait, the list also contains squares of prime numbers. We do not want to count them as intersections. But we can, once we have the list [1,2,3,5,6,10...], go through it this way :

if n is prime : nb_of_sqf += floor(2**50/n^2)
else : nb_of_sqf -= floor(2**50/n^2)

> **Lster said:**
> 
I'll implement that when I get home from my Physics Practical. Don't you hate exams? ;)

Good luck !
Who likes exams ? :)

---

### Post by Lster on 2008-05-15
Back. The exam went fine, thanks for the luck. :D

I'll write the program in C now!

---

### Post by Lux Perpetua on 2008-05-15
I have a working C++ implementation of mine and Lster's ideas. I tested it pretty thoroughly, so I'm pretty sure its results are correct (and it agrees very well with the 6/pi^2 formula). It runs with N = 2^50 in 16-17 seconds on my Intel laptop with the processor set to 800 MHz, which I think is decent. 

The most nontrivial part for me, as I predicted above, was computing the squarefree numbers up to 2^25. My first few implementations were spectacularly inefficient. Even this implementation is too slow if I compile with the wrong flags (say, -g and not -O3) (it would take minutes as opposed to seconds, and the Project Euler website clearly states that no solution should take more than 1 minute on a "modest" computer). My code isn't heavily optimized; I'm sure it could be made to run a lot faster, for example, by special-casing small primes as is often done in implementations of the Sieve of Eratosthenes.

---

### Post by Bichromat on 2008-05-16
> **Lux Perpetua said:**
> I have a working C++ implementation of mine and Lster's ideas. I tested it pretty thoroughly, so I'm pretty sure its results are correct (and it agrees very well with the 6/pi^2 formula). It runs with N = 2^50 in 16-17 seconds on my Intel laptop with the processor set to 800 MHz, which I think is decent. 

The most nontrivial part for me, as I predicted above, was computing the squarefree numbers up to 2^25. My first few implementations were spectacularly inefficient. Even this implementation is too slow if I compile with the wrong flags (say, -g and not -O3) (it would take minutes as opposed to seconds, and the Project Euler website clearly states that no solution should take more than 1 minute on a "modest" computer). My code isn't heavily optimized; I'm sure it could be made to run a lot faster, for example, by special-casing small primes as is often done in implementations of the Sieve of Eratosthenes.

That's FAST. I'm interested. Could you send it to me ? I tried to generate the list of square-free numbers up to 2^25 in C with GMPlib but, being a beginner in C, I think I didn't create the array of mpz_t properly and it crashes near the end...

---

### Post by Lster on 2008-05-16
I'd also like to see that - perhaps you could post it? :)

I'm still working on my solution - I had another exam this morning, slowing my progress. :(

---

### Post by nvteighen on 2008-05-16
> **Lster said:**
> I'd also like to see that - perhaps you could post it? :)

I'm still working on my solution - I had another exam this morning, slowing my progress. :(
I wanted to put some input on this... but not too much plenty of time on here too preparing an oral presentation for a university course.

Hope you're doing well on your exams!

---

### Post by happyhamster on 2008-05-16
> **Lster said:**
> I'm still working on my solution - I had another exam this morning, slowing my progress. :(
Err, are you sure it's not the other way around: the evil Euler Project is hampering your academic progress :P

---

### Post by Lster on 2008-05-16
[QUOTE=nvteighen]I wanted to put some input on this... but not too much plenty of time on here too preparing an oral presentation for a university course.

Hope you're doing well on your exams![/QUOTE]

Thanks. :) Hope your oral presentation goes well too! Luckily none of my exams involve speaking... I'm terrible at it!

My program is set off running - I will have the results in moments... :D

---

### Post by Lster on 2008-05-16
[QUOTE=happyhamster]Err, are you sure it's not the other way around: the evil Euler Project is hampering your academic progress :P[/QUOTE]

Well I've been getting pure A grades so far... :D

---

### Post by nvteighen on 2008-05-16
> **Lster said:**
> Thanks. :) Hope your oral presentation goes well too! Luckily none of my exams involve speaking... I'm terrible at it!

My program is set off running - I will have the results in moments... :D
Thanks... 

(...Well, I'm also still struggling with Programming Challenge 10: Accurate floats ([http://ubuntuforums.org/showthread.php?t=783653&](http://ubuntuforums.org/showthread.php?t=783653&)) in C ;) My initial approach was so silly and overcomplicated that I've started again from scratch... Yes, yes, Python can be easier...)

---

### Post by Lster on 2008-05-16
I haven't been able to get this to work yet! I'm using the method Bichromat suggested:

[QUOTE=Bichromat]if n is prime : nb_of_sqf += floor(2**50/n^2)
else : nb_of_sqf -= floor(2**50/n^2)[/QUOTE]

I calculate the SquareFrees to be an array of squarefree numbers less than 2^25 with LengthSF to be the number of (used) elements in the array. Surely this code is correct then:

[PHP]unsigned long Total = 0;
for ( I = 0 ; I < LengthSF ; I ++ )
{
	if ( IsPrime ( SquareFrees [ I ] ) )
		Total += M / ( SquareFrees [ I ] * SquareFrees [ I ] );
	else
		Total -= M / ( SquareFrees [ I ] * SquareFrees [ I ] );
	
	if ( I % 1000 == 0 ) printf ( "%li / %li\n" , I , LengthSF );
}[/PHP]

It's plenty fast enough with O3 optimization (the whole process take less than 50 seconds), but the answer doesn't seem correct (according to Project Euler). I've checked that the squarefree numbers are indeed correct and they appear to be.

Lux Perpetua, how many squarefree numbers do you make under 2^25? I make 20398664. That would be a useful check! ;)

---

### Post by Bichromat on 2008-05-16
Actually, the sqf in the equation you quoted stands for squareful (I know, it's dumb). 
So, Total should be initialized to 2^50-1 and then :

```

    if ( IsPrime ( SquareFrees [ I ] ) )
        Total -= M / ( SquareFrees [ I ] * SquareFrees [ I ] );
    else
        Total += M / ( SquareFrees [ I ] * SquareFrees [ I ] );

```

---

### Post by Lux Perpetua on 2008-05-16
> **Lster said:**
> I haven't been able to get this to work yet! I'm using the method Bichromat suggested:



I calculate the SquareFrees to be an array of squarefree numbers less than 2^25 with LengthSF to be the number of (used) elements in the array. Surely this code is correct then:

[PHP]unsigned long Total = 0;
for ( I = 0 ; I < LengthSF ; I ++ )
{
	if ( IsPrime ( SquareFrees [ I ] ) )
		Total += M / ( SquareFrees [ I ] * SquareFrees [ I ] );
	else
		Total -= M / ( SquareFrees [ I ] * SquareFrees [ I ] );
	
	if ( I % 1000 == 0 ) printf ( "%li / %li\n" , I , LengthSF );
}[/PHP]

It's plenty fast enough with O3 optimization (the whole process take less than 50 seconds), but the answer doesn't seem correct (according to Project Euler). I've checked that the squarefree numbers are indeed correct and they appear to be.

Lux Perpetua, how many squarefree numbers do you make under 2^25? I make 20398664. That would be a useful check! ;)Confirmed!

However, your code for updating Total isn't correct. The plus/minus doesn't depend only on whether the divisor is prime. For example, going back to my first post in this thread, you'd need to add M/(30^2), even though 30 isn't prime. 30 actually has three prime factors: 2, 3, and 5. Hint: if you've ever heard of the "inclusion-exclusion principle," this is it.

---

### Post by Lster on 2008-05-17
I haven't heard of it, but I know what you mean - I think. I'll test it out!

---

### Post by Lster on 2008-05-17
Cracked! :popcorn:

I takes almost a minute in unoptimized C with O3. I now only subtract a number if it has an even number of factors and add it if it has an odd number of factors.

Well I'm open to code requests if anyone would like. And thanks to everyone who gave advice... :D

---

### Post by Bichromat on 2008-05-17
> **Lster said:**
> Cracked! :popcorn:

I takes almost a minute in unoptimized C with O3. I now only subtract a number if it has an even number of factors and add it if it has an odd number of factors.

Well I'm open to code requests if anyone would like. And thanks to everyone who gave advice... :D

I'd like to see it ! Because I can't even manage to compute the squarefree under 2^25 in a reasonable time :(

As for the even/odd number of factors, could someone explain it to me ?

---

### Post by Lster on 2008-05-17
I had never heard of the Inclusion-Exclusion Principle but none the less I never what it was really about. It's actually quite simple; it avoids double counting by removing every other intersection.

For example with the trivial intersection up to 100, finding the number of integers divisible by 4 or 9. It is of course 100/4 + 100/9 - 100/(4*9) (assuming / rounds down).

You can expand that sequence of intersections and it turns out that every other intersection should be removed from the total.

Remember I posted this... These are the intersections:

[LIST=1]
[*]a
[*]a + b - ab
[*]a + b + c - ab - ac - bc + abc
[*]a + b + c + d - ab - ac - ad - bc - bd - cd + abc + abd + acd + bcd - abcd
[/LIST]

a, b, c, d... are all relatively prime (as they are distinct primes squared). So the set a is simply n/a. The set ab is similarly n/(ab). Et cetera...

So effectively going through the sets is like adding or taking the following (but this only goes up to d):

[LIST=1]
[*]a + b + c + d ...
[*]- ab - bc - ac - ad - bd - cd ...
[*]abc + abd + acd + bcd
[/LIST]

Each one you take has a multiple of 2 factors; each one you add has an odd number of factors.

Have a look at:
[http://en.wikipedia.org/wiki/Inclusion_exclusion](http://en.wikipedia.org/wiki/Inclusion_exclusion)

---

### Post by Bichromat on 2008-05-17
OK, I looked at the graph in the Wikipedia article and it became obvious

---

### Post by Lux Perpetua on 2008-05-17
Awesome. Time for show and tell? :-)

I managed to get it down to about 7.45 seconds on my machine. I'm embarrassed to think of how many things I tried before arriving at this. ```

#include <iostream>
#include <cmath>

using namespace std;

int main(void) {
    int64_t N = 1;
    N <<= 50;
    int n(sqrt(N));

    char *buffer = new char[n];
    char *table = buffer-1;
    /* if table[k] < 0, then k is not squarefree; otherwise,
       table[k] is the number of prime factors of k. */

    int lim(sqrt(n));

    /* sieve of Eratosthenes modified
       to catch the squarefree numbers */

    for (int p = 2; p <= n; p += 1)  {
        if (table[p]) continue;

        if (p <= lim) {
            int s = p*p;
            for (int k = s; k <= n; k += s)
                table[k] = -1;
        }

        for (int k = p; k <= n; k += p)
            if (table[k] >= 0)
                ++table[k];
    }

    int64_t total = 0;

    for (int k = 1; k <= n; ++k) {
        int64_t s = k;
        s *= k;
        s = N/s;

        if (table[k] >= 0)
            total += (table[k]&1)? -s : s;
    }
    cout << total << endl;

    delete [] buffer;

    return 0;
}
```

---

### Post by Bichromat on 2008-05-17
Truly amazing ! =D>

---

### Post by Lster on 2008-05-17
Of course as your solution shows, you don't actually need a list of primes. A couple of improvements and mine now computes in 3 seconds on my computer:

EDIT: I've improved the code again...

[PHP]
#include "stdlib.h"
#include "stdio.h"
#include "math.h"
#include "string.h"

const long N = 33554432; // 2^25
const long M = 1125899906842624; // 2^50


int main ( void )
{
	printf ( "Sieving and listing squarefrees...\n" );
	
	char * Sieve = malloc ( N * sizeof ( char ) );
	if ( Sieve == 0 ) return 1;
	memset ( Sieve , 0 , N * sizeof ( char ) );
	
	long I , J , D;
	
	for ( J = 4 ; J < N ; J += 4 ) Sieve [ J ] = -1;
	for ( I = 3 ; I < N ; I += 2 )
	{
		D = I * I;
		for ( J = D ; J < N ; J += D ) Sieve [ J ] = -1;
	}
	
	for ( I = 2 ; I < N ; I ++ )
	{
		if ( Sieve [ I ] != 0 ) continue;
		
		for ( J = I ; J < N ; J += I )
			if ( Sieve [ J ] >= 0 )
				Sieve [ J ] ++;
	}
	
	printf ( "Totalling squarefrees under 2^50...\n" );
	
	long Total = M;
	for ( I = 2 ; I < N ; I ++ )
	{
		if ( Sieve [ I ] < 0 ) continue;
		
		D = M / ( I * I );
		if ( Sieve [ I ] & 1 )
			Total -= D;
		else
			Total += D;
	}
	
	printf ( "Answer = %li\n" , Total );
	
	return 0;
}
[/PHP]

---

### Post by nvteighen on 2008-05-17
@Lux Perpetua: your code needs 5 secs on my machine (Centrino Duo 1.7 GHz)

@Lster: cannot compile because M being too long. Changing to "long long" isn't enough... Are you using a 64-bit machine?

---

### Post by Lster on 2008-05-17
Yes, I'm on a 64bit processor... I'm not quite sure how to fix that. I think Bichromat managed to run it, maybe he would give you details?

---

### Post by Bichromat on 2008-05-17
You need to change every long to long long AND add the LL suffix to the constant 2^50 to make it work.
The winner on my machine, with -O3, is Lux Perpetua, with 7.0s. Lster is just behind with 8.8s. Will he manage to climb to the first place ? :popcorn:

---

### Post by Lster on 2008-05-17
Yes. If you have a dual core... I'm parallelizing my algorithm to take advantage of extra CPUs! It's already a good 15% faster than Lux Perpetua's solution. I should be able to get it down to within 2 second... When I do I'll post the code! :)

---

### Post by Bichromat on 2008-05-17
My core 2 duo will have fun ! :D

Edit : By the way, by using 32 bits ints for variables that are not > 2^31-1, and stopping the second loop when I>sqrt(N), I managed to get your code to run in a bit less than 7.0s.

---

### Post by Bichromat on 2008-05-18
Switching to unsigned ints improved the timing: your program is down to 6.5s on my machine (with frequency fixed to 800MHz). Looking for a way to make the code portable between 32/64 bits architectures, I found the "stdint.h" header: it defines 8, 16, 32 and 64 bits integers regardless of the platform. But I don't know how your computer will react to "%lli"...

```

#include "stdlib.h"
#include "stdio.h"
#include "math.h"
#include "stdint.h"


int main ( void )
{

    uint64_t M = pow(2,50); // 2^50
    uint64_t Total = M;
    uint64_t K, H;

    uint32_t N = sqrt(M); // 2^25
    uint32_t G = sqrt(N);
    uint32_t D, I, J;
    
    int8_t * Sieve = calloc ( N, sizeof ( int8_t ) );
    if ( Sieve == 0 ) return 1;

    //Sieving and listing squarefrees...
    // -1 indicates squareful numbers

    for ( J = 4 ; J <= N ; J += 4 ) Sieve [ J ] = -1;
    for ( I = 3 ; I <= G ; I += 2 )
    {
        D = I * I;
        for ( J = D ; J <= N ; J += D ) Sieve [ J ] = -1;
    }
    
    for ( I = 2 ; I <= N ; ++I )
    {
        if ( Sieve [ I ] != 0 ) continue;
        
        for ( J = I ; J <= N ; J += I )
            if ( Sieve [ J ] != -1 )
                Sieve [ J ] += 1;
    }
    
    //Totalling squarefrees under 2^50...
    
    for ( K = 2 ; K <= N ; ++K )
    {
        if ( Sieve [ K ] < 0 ) continue;
        
        H = M / (K * K);
        if ( Sieve [ K ] & 1 )
            Total -= H;
        else
            Total += H;
    }
    
    printf ( "Answer = %lli\n" , Total );
    
    return 0;
}

```

---

### Post by Lster on 2008-05-18
Here's some multi-threaded code to play with. It gives a slight improvement on my Core 2 T7300, running in about 2.35 seconds. Without threading it takes about 2.5 (equal to Luz Perpetua's).

[PHP]
#include "stdlib.h"
#include "stdio.h"
#include "math.h"
#include "string.h"
#include "pthread.h"

const long N = 1125899906842624;
const long M = 33554432;

char * Sieve;
long Total;
long Return = 0;

volatile long Sync0 = 1 , Sync1 = 1;

void * SecondThreadFunc ( void * Args )
{
	long I , J , D;
	
	for ( J = 2 ; J < M ; J += 2 )
		if ( Sieve [ J ] >= 0 )
			Sieve [ J ] ++;
	
	for ( J = 4 ; J < M ; J += 4 )
		Sieve [ J ] = -1;
	
	Sync1 = 0;
	while ( Sync0 );
	
	for ( I = 3 ; I < M ; I += 2 )
	{
		if ( Sieve [ I ] < 0 ) continue;
		
		D = N / ( I * I );
		if ( Sieve [ I ] & 1 )
			Return -= D;
		else
			Return += D;
	}
}

int main ( void )
{
	Sieve = calloc ( M , sizeof ( char ) );
	if ( Sieve == 0 ) return 1;
	
	printf ( "Sieving (2 threads)...\n" );
	pthread_t SecondThread;
	pthread_create ( & SecondThread , 0 , SecondThreadFunc , 0 );
	
	long I , J , D;
	for ( I = 3 ; I < M ; I += 2 )
	{
		if ( Sieve [ I ] ) continue;
		
		D = I * I;
		for ( J = D ; J < M ; J += D )
			Sieve [ J ] = -1;
		
		for ( J = I ; J < M ; J += I )
			if ( Sieve [ J ] >= 0 )
				Sieve [ J ] ++;
	}
	
	Total = N;
	Sync0 = 0;
	while ( Sync1 );
	
	printf ( "Totalling (2 threads)...\n" );
	
	for ( I = 2 ; I < M ; I += 2 )
	{
		if ( Sieve [ I ] < 0 ) continue;
		
		D = N / ( I * I );
		if ( Sieve [ I ] & 1 )
			Total -= D;
		else
			Total += D;
	}
	
	pthread_join ( SecondThread , 0 );
	Total += Return;
	
	printf ( "Answer = %li\n" , Total );
	
	return 0;
}
[/PHP]

---

### Post by nvteighen on 2008-05-18
@Bichromat: yours worked! Aprox. 6 secs on my machine.

@Lster: what's the library for pthread.h? I have to install it first.

---

### Post by Bichromat on 2008-05-18
> **nvteighen said:**
> @Bichromat: yours worked! Aprox. 6 secs on my machine.

@Lster: what's the library for pthread.h? I have to install it first.
Di you try to compile with -lpthread ?

---

### Post by nvteighen on 2008-05-18
I was missing -lpthread, but it gives me following warnings to Lster's code:

1. M is still too long (const long long doesn't work either).

2. SecondThreadFunc is not returning any void pointer, being of type void*.

---

### Post by Lster on 2008-05-18
[QUOTE=Bichromat]You need to change every long to long long AND add the LL suffix to the constant 2^50 to make it work.[/QUOTE]

Does that fix the first warning? I think technically SecondThreadFunc should return something like:

( void * ) 0

Maybe that would be a fix to the second solution?

---

### Post by nvteighen on 2008-05-18
> **Lster said:**
> Does that fix the first warning? I think technically SecondThreadFunc should return something like:

( void * ) 0

Maybe that would be a fix to the second solution?
There it is! (I was forgetting the LL suffix)

Well, it leads to 100% CPU usage in both cores for aprox. 7 secs.

And in turn, this helped me to discover how to solve a bug in something I'm working on... I was transforming a string to long long with atoi() instead of atoll()!

---

### Post by Bichromat on 2008-05-18
I get no warning about SecondThreadFunc. Things to change :
- N, Total, Return, I, J, D must be "long long"
- append LL to 2^50
- change the format in printf : "%lli" or "%lld"

There's one thing I don't understand. The variable 'I' appears to be less than M all the time, but if I don't declare it as a long long, the program segfaults. :confused:

Edit : too late

Also, J<M should really be J<=M.

---

### Post by Lster on 2008-05-18
[QUOTE=Bichromat]There's one thing I don't understand. The variable 'I' appears to be less than M all the time, but if I don't declare it as a long long, the program segfaults.[/QUOTE]

That's because I is squared in the last loop! :)

I'm on Project Euler 142 now after doing 169. It's proving quite tricky too. :)

---

### Post by Bichromat on 2008-05-18
> **Lster said:**
> That's because I is squared in the last loop! :)

C must have an odd way of converting between integer types...

> **Lster said:**
> I'm on Project Euler 142 now after doing 169. It's proving quite tricky too. :)

Hmm, it looks interesting too :)

---

### Post by Lster on 2008-05-18
[QUOTE=Bichromat]Hmm, it looks interesting too :)[/QUOTE]

I've solved it now. :) Interested enough for a solution?

---

### Post by Bichromat on 2008-05-18
No, I'll try to find it myself ;-)

---

### Post by Lux Perpetua on 2008-05-18
> **Bichromat said:**
> But I don't know how your computer will react to "%lli"...I *think* (I'm not 100% sure) that the 'll' modifier is specified by C99. In any case, I receive no complaints from your code if I compile with the flag -std=c99 instead of -ansi.

---

### Post by Bichromat on 2008-05-18
> **Lux Perpetua said:**
> I *think* (I'm not 100% sure) that the 'll' modifier is specified by C99. In any case, I receive no complaints from your code if I compile with the flag -std=c99 instead of -ansi.

long long ints were added in C99, so the "ll" format must come from the same standard.

---

