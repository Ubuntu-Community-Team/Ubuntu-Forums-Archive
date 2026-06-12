---
title: "fastest algo to calculate nCr"
date: 2011-01-23
forum: Programming Talk
---

### Post by c2tarun on 2011-01-23
What is the fastest algo we can make to calculate

nCr
!n/(!r * !(n-r))

Thanks

---

### Post by trent.josephsen on 2011-01-23
I think you mean n! / (r! * (n-r)!)

The first observation I made is that r! will cancel with the first terms of n!, saving you potentially quite a number of calculations.  That leaves you with

( n*(n-1)*[...]*(r+1) ) / ( (n-r)*(n-r-1)*[...]*1 )

The numerator and denominator have the same number of terms and can be calculated iteratively at the same time.  I wrote pseudocode, but then it occurred to me that this might be a homework problem and I wouldn't want to do all your work for you.

The other observation is that this technique saves you the most calculation when r > (n-r).  Fixing that is also left as an exercise for the reader, because, frankly, I'm lazy.

Whether or not this is the "fastest" algorithm, I have no idea.  Beats taking three factorials by a little, and it beats recursively generating Pascal's triangle by a lot (although if you have a lot of these to do, you might save time by generating it once and doing lookups into it).

---

### Post by c2tarun on 2011-01-23
> **trent.josephsen said:**
> I think you mean n! / (r! * (n-r)!)

The first observation I made is that r! will cancel with the first terms of n!, saving you potentially quite a number of calculations.  That leaves you with

( n*(n-1)*[...]*(r+1) ) / ( (n-r)*(n-r-1)*[...]*1 )

The numerator and denominator have the same number of terms and can be calculated iteratively at the same time.  I wrote pseudocode, but then it occurred to me that this might be a homework problem and I wouldn't want to do all your work for you.

The other observation is that this technique saves you the most calculation when r > (n-r).  Fixing that is also left as an exercise for the reader, because, frankly, I'm lazy.

Whether or not this is the "fastest" algorithm, I have no idea.  Beats taking three factorials by a little, and it beats recursively generating Pascal's triangle by a lot (although if you have a lot of these to do, you might save time by generating it once and doing lookups into it).

Thanks for replying. This is not my homework problem ;)
This is a problem came in january cook off of [www.codechef.com](www.codechef.com)
I tried to solve but my program was too slow.
Here is what i did:
```

scanf("%d%d",&a,&b);
        c=a-b;
        if(c>b)
        {
            temp=b;
            b=c;
            c=temp;
        }
        num=den=1;
        for(i=b+1;i<=a;i++)
            num*=i;
        for(i=2;i<=c;i++)
            den*=i;
        printf("%d\n",num/den);

```
Can you suggest any improvement in this code so as to increase its speed?
Thanks

---

### Post by worksofcraft on 2011-01-23
> **c2tarun said:**
> Thanks for replying. This is not my homework problem ;)
This is a problem came in january cook off of [www.codechef.com](www.codechef.com)
I tried to solve but my program was too slow.
Here is what i did:
```

scanf("%d%d",&a,&b);
        c=a-b;
        if(c>b)
        {
            temp=b;
            b=c;
            c=temp;
        }
        num=den=1;
        for(i=b+1;i<=a;i++)
            num*=i;
        for(i=2;i<=c;i++)
            den*=i;
        printf("%d\n",num/den);

```
Can you suggest any improvement in this code so as to increase its speed?
Thanks

I think you did very well and I never heard of faster algorithms for this. My concern would not be with speed but with numeric overflow, because you very soon be dividing very large numbers with each other, so the result might fit in an int but the num and den might not! :shock:

---

### Post by c2tarun on 2011-01-23
> **worksofcraft said:**
> I think you did very well and I never heard of faster algorithms for this. My concern would not be with speed but with numeric overflow, because you very soon be dividing very large numbers with each other, so the result might fit in an int but the num and den might not! :shock:

Thanks :)
I'll try to use bigger variable types for num and den.

---

### Post by trent.josephsen on 2011-01-23
You have implemented my first suggestion, but not my second.

```
for(i=b+1;i<=a;i++) /* runs for (a - b) iterations */
      num*=i;
```
and with a slight adjustment
```
for(i=1;i<=c;i++) /* runs for c == (a - b) iterations */
      den*=i;
```
A little rewrite can perform both calculations in the same for loop, at the expense of some extra fiddling to calculate the right factors.

Hmm... halving the number of tests and branches is tempting...  it's probably worth it, but you'd have to benchmark it to know for sure.

Another technique would be to generate Pascal's Triangle on the fly and use it to look up combinations that have already been calculated.  This would improve performance only if you have quite a number of combinations to determine, all within a relatively small range; e.g., once you'd looked up (say) 7c3, then 5c2 could be done in constant time, and 8c3 could be done in linear time.  Calculating the first one would take O(n * k) time, though, and you might run into memory trouble with very large numbers; I don't much fancy figuring 9999c1 this way.

---

### Post by worksofcraft on 2011-01-23
> **c2tarun said:**
> Thanks :)
I'll try to use bigger variable types for num and den.

```

       c=a-b;
        if(c>b)
        {
            temp=b;
            b=c;
            c=temp;
        }
        num=den=1;
        for(i=b+1;i<=a;i++)
            num*=i;
        for(i=2;i<=c;i++)
            den*=i;

```
I not thought this through, but in both "for" loops there, you have "c" iterations and if you line them up properly you can do a multiplication and a division together in each step.

---

### Post by c2tarun on 2011-01-23
> **trent.josephsen said:**
> You have implemented my first suggestion, but not my second.

```
for(i=b+1;i<=a;i++) /* runs for (a - b) iterations */
      num*=i;
```and with a slight adjustment
```
for(i=1;i<=c;i++) /* runs for c == (a - b) iterations */
      den*=i;
```A little rewrite can perform both calculations in the same for loop, at the expense of some extra fiddling to calculate the right factors.

Hmm... halving the number of tests and branches is tempting...  it's probably worth it, but you'd have to benchmark it to know for sure.

Another technique would be to generate Pascal's Triangle on the fly and use it to look up combinations that have already been calculated.  This would improve performance only if you have quite a number of combinations to determine, all within a relatively small range; e.g., once you'd looked up (say) 7c3, then 5c2 could be done in constant time, and 8c3 could be done in linear time.  Calculating the first one would take O(n * k) time, though, and you might run into memory trouble with very large numbers; I don't much fancy figuring 9999c1 this way.

I don't know much about the pascal's triangle method, but I would like to learn. Can you please explain a bit or refer me to any online article for this concept.
Thanks

---

### Post by c2tarun on 2011-01-23
> **worksofcraft said:**
> ```

       c=a-b;
        if(c>b)
        {
            temp=b;
            b=c;
            c=temp;
        }
        num=den=1;
        for(i=b+1;i<=a;i++)
            num*=i;
        for(i=2;i<=c;i++)
            den*=i;

```I not thought this through, but in both "for" loops there, you have "c" iterations and if you line then up properly you can do a multiplication and a division together in each step.

Ya you are right, we can do that too. but I don't think that'll reduce the number of steps, but it will prevent my from accessing large numbers :)
pretty handy suggestion 
Thanks

---

### Post by trent.josephsen on 2011-01-24
[http://en.wikipedia.org/wiki/Pascal's_triangle](http://en.wikipedia.org/wiki/Pascal's_triangle)

The relevance of Pascal's triangle is that nCk is the kth element (counting from 0) in the nth row (again, counting from 0) in the triangle.

Naively, you might write (Python, hopefully it gets the point across):
```
def pascal(n, k):
    if k == 0 or k == n:
    	return 1
    else:
        return pascal(n-1, k-1) + pascal(n-1, k)
```
This indeed works, but try working it out on paper -- you'll see that **lots** of those calculations are done over and over and over.  I added a line to print the calculation for each recursive call and ran it on 6c2 (colorized to show the repetition):
```
6c2 = 5c1 + 5c2
5c1 = 4c0 + 4c1
[COLOR="Blue"]**4c1**[/COLOR] = 3c0 + 3c1
[COLOR="Red"]**3c1**[/COLOR] = 2c0 + 2c1
[COLOR="Green"]**2c1**[/COLOR] = 1c0 + 1c1
5c2 = 4c1 + 4c2
[COLOR="blue"]**4c1**[/COLOR] = 3c0 + 3c1
[COLOR="red"]**3c1**[/COLOR] = 2c0 + 2c1
[COLOR="Green"]**2c1**[/COLOR] = 1c0 + 1c1
4c2 = 3c1 + 3c2
[COLOR="red"]**3c1**[/COLOR] = 2c0 + 2c1
[COLOR="green"]**2c1**[/COLOR] = 1c0 + 1c1
3c2 = 2c1 + 2c2
[COLOR="green"]**2c1**[/COLOR] = 1c0 + 1c1
```

Consider how many times 10c4 might have to do this and it gets even more ridiculous.  20c10 starts to look laggy.  30c15 takes far longer than I care to wait.

A partial solution is to cache function calls in some sort of hashtable or matrix, so you can look up values that have already been calculated.  Rather than try to work out the best data structure for this application, I just used one of Python's built-in dictionaries indexed on a tuple (n,k).  Again, hopefully the code will be clearer:

```
cache = {}

def pascal(n, k):
    if k == 0 or k == n:
    	return 1
    elif (n,k) in cache:
        return cache[(n,k)]
    else:
    	value = pascal(n-1, k-1) + pascal(n-1, k)
	cache[(n,k)] = value
	return value
```
This version checks if pascal(n,k) has been called before with the same values of n and k.  If it has, it uses the stored value from the previous call.  Otherwise, it recursively calculates a new value and stores it in the lookup table.

This new version shows almost no lag on my machine all the way up to n=500,k=250 or so, even when it has to build the entire triangle to get the result -- it saves time by calculating each term exactly once.

That's not to say it's without its own problems.  pascal(1000,500) exceeded Python's maximum recursion depth when run with an empty cache.  Even if you can avoid that problem, you're still doing things the hard way -- for sufficiently large n, the simple formula at O(n) is always going to beat out generating n rows of Pascal's Triangle at O(n^2).  What might make this solution faster than the iterative, non-caching one is when you have many problems to solve, because you can treat previous solutions as partial solutions to the new problem.

With an eye toward improvement, I'd like to note that Pascal's Triangle is symmetric:  nCk == nC(n-k).  This means we can get away with searching and storing only half of it.  Furthermore, nC1 = n, nC2 = (n*(n-1))/2, and you could find equations for other values of k as well.  A dictionary probably doesn't offer the best lookup times, either -- something specialized could probably outperform it.

*yawn* I'm done for today.

---

### Post by c2tarun on 2011-01-24
> **trent.josephsen said:**
> [http://en.wikipedia.org/wiki/Pascal's_triangle]("http://en.wikipedia.org/wiki/Pascal%27s_triangle")

The relevance of Pascal's triangle is that nCk is the kth element (counting from 0) in the nth row (again, counting from 0) in the triangle.

Naively, you might write (Python, hopefully it gets the point across):
```
def pascal(n, k):
    if k == 0 or k == n:
        return 1
    else:
        return pascal(n-1, k-1) + pascal(n-1, k)
```This indeed works, but try working it out on paper -- you'll see that **lots** of those calculations are done over and over and over.  I added a line to print the calculation for each recursive call and ran it on 6c2 (colorized to show the repetition):
```
6c2 = 5c1 + 5c2
5c1 = 4c0 + 4c1
[COLOR=Blue]**4c1**[/COLOR] = 3c0 + 3c1
[COLOR=Red]**3c1**[/COLOR] = 2c0 + 2c1
[COLOR=Green]**2c1**[/COLOR] = 1c0 + 1c1
5c2 = 4c1 + 4c2
[COLOR=blue]**4c1**[/COLOR] = 3c0 + 3c1
[COLOR=red]**3c1**[/COLOR] = 2c0 + 2c1
[COLOR=Green]**2c1**[/COLOR] = 1c0 + 1c1
4c2 = 3c1 + 3c2
[COLOR=red]**3c1**[/COLOR] = 2c0 + 2c1
[COLOR=green]**2c1**[/COLOR] = 1c0 + 1c1
3c2 = 2c1 + 2c2
[COLOR=green]**2c1**[/COLOR] = 1c0 + 1c1
```Consider how many times 10c4 might have to do this and it gets even more ridiculous.  20c10 starts to look laggy.  30c15 takes far longer than I care to wait.

A partial solution is to cache function calls in some sort of hashtable or matrix, so you can look up values that have already been calculated.  Rather than try to work out the best data structure for this application, I just used one of Python's built-in dictionaries indexed on a tuple (n,k).  Again, hopefully the code will be clearer:

```
cache = {}

def pascal(n, k):
    if k == 0 or k == n:
        return 1
    elif (n,k) in cache:
        return cache[(n,k)]
    else:
        value = pascal(n-1, k-1) + pascal(n-1, k)
    cache[(n,k)] = value
    return value
```This version checks if pascal(n,k) has been called before with the same values of n and k.  If it has, it uses the stored value from the previous call.  Otherwise, it recursively calculates a new value and stores it in the lookup table.

This new version shows almost no lag on my machine all the way up to n=500,k=250 or so, even when it has to build the entire triangle to get the result -- it saves time by calculating each term exactly once.

That's not to say it's without its own problems.  pascal(1000,500) exceeded Python's maximum recursion depth when run with an empty cache.  Even if you can avoid that problem, you're still doing things the hard way -- for sufficiently large n, the simple formula at O(n) is always going to beat out generating n rows of Pascal's Triangle at O(n^2).  What might make this solution faster than the iterative, non-caching one is when you have many problems to solve, because you can treat previous solutions as partial solutions to the new problem.

With an eye toward improvement, I'd like to note that Pascal's Triangle is symmetric:  nCk == nC(n-k).  This means we can get away with searching and storing only half of it.  Furthermore, nC1 = n, nC2 = (n*(n-1))/2, and you could find equations for other values of k as well.  A dictionary probably doesn't offer the best lookup times, either -- something specialized could probably outperform it.

*yawn* I'm done for today.

awesome tutorial. :)
Thanks a lot

---

### Post by slavik on 2011-01-24
Is this homework? Is it work? Why are you asking such a question?

---

### Post by Arndt on 2011-01-24
> **c2tarun said:**
> What is the fastest algo we can make to calculate

nCr
!n/(!r * !(n-r))

Thanks

Do you need the answer to be exact or only approximate? If only approximate, you can use ordinary floating point numbers and logarithms. If exact, you need something that handles arbitrarily large integers (unless your input set is really restricted). The product a*b can be computed in a variety of ways, and the first one comes to think of will not be optimal. The same probably holds for nCr as a whole.

Maybe these are interesting: [http://www.loria.fr/~zimmerma/mca/mca-cup-0.5.1.pdf](http://www.loria.fr/~zimmerma/mca/mca-cup-0.5.1.pdf), [http://en.wikipedia.org/wiki/Multiplication_algorithm](http://en.wikipedia.org/wiki/Multiplication_algorithm)

---

### Post by c2tarun on 2011-01-24
> **slavik said:**
> Is this homework? Is it work? Why are you asking such a question?

actually this is a problem in one cook off competition on code chef.
Its not home work, I don't go to school ;)

---

