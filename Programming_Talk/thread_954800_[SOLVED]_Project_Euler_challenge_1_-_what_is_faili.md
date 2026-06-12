---
title: "[SOLVED] Project Euler challenge 1 - what is failing ??????? (python)"
date: 2008-10-21
forum: Programming Talk
---

### Post by alberto ferreira on 2008-10-21
I can't solve this:

> If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23. Find the sum of all the multiples of 3 or 5 below 1000.

  

I've searched in the net and this solution works:
[PHP]def multiples_of_3_or_5():
        for number in xrange(1000):
            if not number % 3 or not number % 5:
                yield number

print sum(multiples_of_3_or_5())[/PHP]

But mine doesn't, what's wrong??

[PHP]import sys

#Get integer from sys###
arg = str(sys.argv[1:2])
limit = int(arg[2:-2])
########################

multiples=[3,5]
numbers=[]
i=range(len(multiples))


for n in range(1,limit):
        for i in multiples:
                if n % i == 0:
                        numbers.append(n)

#print numbers
print sum(numbers)[/PHP]

---

### Post by Nemooo on 2008-10-21
Well I don't know Python, so I'll just throw out some pseudo-code:

```
for i 1 1000
    if(i mod 3 0 || i mod 3 == 0)
        sum = sum + i

print sum
```

You're code seems unnecessary complicated.

---

### Post by SteelDragon on 2008-10-21
What do you mean your code doesn't work? Does it give an error? The wrong result?

Issues I see looking at your code:
[LIST]
[*]Why is it so complicated getting the limit from the arguments? It should be enough to use:
```
limit = int(sys.argv[1])
```
[*]Numbers that are multiples of both 3 and 5 (i.e. 15) will be appended and therefore added twice to your final result.[/LIST]

I'm no Python pro, but I did find the solution using Python (and Scheme, thanks to LaRoza).

Good Luck.

---

### Post by alberto ferreira on 2008-10-21
It gives the wrong number. Ahhh I see! I was doubling some of the results lol, thanks, I'll try it and if it doesn't work I'll have to bother you again ;) 


And about getting the limit - I'm a newb so I just added code until it worked :), but how would you do it to prevent error from happening if the user didn't pass an integer as argument?

Thanks

---

### Post by SteelDragon on 2008-10-21
LOL @ adding code until it works.

You don't prevent the error, you just catch it when it is raised.
Try this:
[http://linuxgazette.net/issue83/evans.html]("http://linuxgazette.net/issue83/evans.html")

I would recommend trying out the [Beginner Programming Challenges]("http://ubuntuforums.org/showthread.php?t=876494&highlight=beginner") on these boards, from which I was directed to that link. They've been very helpful for me, so far. The only downside is that I've abandoned the project I wanted Python for in the first place in favour of playing around with stuff I learned in the challenges. :)

The challenges have sort of drifted out of popularity lately, but by the time you finish them all, you should have a solid footing in Python, after which Project Euler can be about the problem-solving rather
than syntax, which makes it much more fun, IMO.

---

### Post by alberto ferreira on 2008-10-21
Thanks! Could someone try solving the first problem? because it's saying :wrong result
over and over

[http://projecteuler.net/index.php?section=problems&id=1](http://projecteuler.net/index.php?section=problems&id=1)

I would greatly appreciate it, here's my code by the way:
[php]import sys

limit = int(sys.argv[1])

multiples=[3,5]
numbers=[]
i=range(len(multiples))

for n in range(1,limit):
    for i in multiples:
        if n % i == 0 and numbers[-1:] != [n]:
            numbers.append(n)

#numbers = set(numbers) ## This line is no longer needed now that duplicates are tested
print sum(numbers)[/php]And I'll follow your advice into training python

---

### Post by namegame on 2008-10-21
> **alberto ferreira said:**
> Thanks! Could someone try solving the first problem? 


EDIT: I decided to do it in C, b/c I am most familiar with it.

[php]
#include <stdio.h>  
#include <stdlib.h>

int main(){

   int sum = 0;
   int i;

   for (i = 1; i < 1000; i++){
      if (i % 5 == 0 || i % 3 == 0)
         sum = sum + i;
   }

   fprintf(stdout, "%d\n", sum);

   return EXIT_SUCCESS;
}
[/php]

I got the right answer as well.

---

### Post by cx323 on 2008-10-21
here's my solution in python:

```
print sum( [i for i in range(1000) if not i % 3 or not i % 5] )
```

---

### Post by Gilabuugs on 2008-10-21
This is really a matter of learning the language before you attempt it, as the project euler problems grow much harder quickly

the python website has many helpful books tutorials and a wonderful reference
[PHP]#!/usr/bin/env python
sum = 0
for i in xrange(1000):
    if i % 3 == 0 or i % 5 == 0:
        sum = sum + i
print sum[/PHP]

---

### Post by dwhitney67 on 2008-10-21
> **cx323 said:**
> here's my solution in python:

```
print sum( [i for i in range(1000) if not i % 3 or not i % 5] )
```
Sweet and compact solution.  But not very robust.

If Project Euler had an additional challenge, say one of finding the sum of the natural numbers below a value N, with values v1, v2, ..., vM, then your solution would need to be modified.  My question to you is... why not create the more robust solution in the first place?

Even though Alberto Ferreira admits he's a Python newb, his final solution is closer to the (new/modified "dwhitney") target than yours.

Alberto -

For grins, add/replace the following in your code:
```

if (len(sys.argv) < 3):
        print "Usage: ", sys.argv[0], " <limit> <value1> [<value2> ... <valueN>]"
        sys.exit()

limit = int(sys.argv[1])

multiples = []

for n in range(2, len(sys.argv)):
        multiples.append( int(sys.argv[n]) );
...

```

Then test your code with 3 command-line arguments:
```
euler1.py 10 3 5
euler1.py 1000 3 5
```

---

### Post by slavik on 2008-10-22
wasn't there a solution not needing any programming at all?

999 / 3 = 333 numbers (3, 6, ..., 996, 999)
now, divide the whole series by 3, you get 1, 2, ..., 330, 333
the famous formula n/2 * (n+1) = 333 * 167 = 55611, multiply by 3 and you get: 166833 (sum of all multiples of 3)

995 / 5 = 199 (5, 10, ..., 990, 995), divide by 5 == (1, 2, ..., 198, 199)
formula = 200 * 100 * 5 = 100000

above two added = 266833

subtract sum of multiples of 15 which is 33 * 67 * 15 = 33165

you get the result of 233668

---

### Post by alberto ferreira on 2008-10-22
I don't know why but I haven't changed my answer to the problem but already works, maybe it was a problem in the server? :s


I saved the compact python algoritm, the C algoritm and the multiple argument algoritm. I also loved slavik's solution for it's mathematical feat.

Thanks to everyone!

---

### Post by namegame on 2008-10-22
> **alberto ferreira said:**
>  I also loved slavik's solution for it's mathematical feat.



That way is definitely more efficient and elegant.

I can foresee issues with my program with extremely large numbers.

---

### Post by y-lee on 2008-10-22
> **alberto ferreira said:**
> I also loved slavik's solution for it's mathematical feat.

Thanks to everyone!

slaviks solution is pretty similar to the [solution i gave ]("http://ubuntuforums.org/showpost.php?p=5635830&postcount=34") here elsewhere. And as to generalizing my solution generalguy gave a really [elegant version]("http://ubuntuforums.org/showpost.php?p=5636471&postcount=35") of that one :)

---

