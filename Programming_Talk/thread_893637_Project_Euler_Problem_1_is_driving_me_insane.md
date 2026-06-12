---
title: "Project Euler Problem 1 is driving me insane"
date: 2008-08-18
forum: Programming Talk
---

### Post by MONODA on 2008-08-18
I just cant seem to figure it out. I have been trying it all morning but cant seem to get the correct answer. I am starting to think that I am not even answering the question properly. I am not asking you to give me the answer but to just comment on my code and help me make it more efficient and simpler since it really isnt well written.

[http://projecteuler.net/index.php?section=problems&id=1](http://projecteuler.net/index.php?section=problems&id=1)

written in python:
[PHP]def multi(x): 
        var = 0
        add = 0
        for y in range(0, 1000, x):
                print y
                add += 3
                var += add
        print var
three = multi(3)
five = multi(5)
three
five
[/PHP]
I tried to add the variables "three" and "five" but it turns out they are NoneTypes. What does that mean and how can I fix it. Thanks, I am really strugling with python, it's my first real experience with programming.

---

### Post by howlingmadhowie on 2008-08-18
you haven't set the variables three and five. try replacing the line "print var" with "return var"

as it is, i'm not sure your algorithm is right, but this tip should help you debug it :)

---

### Post by Lster on 2008-08-18
Why don't you just go through every integer, x,  between the values 1 and 999 (inclusive). Keep a total variable and for each x, test whether it is divisible by 3 or 5 and only add it to the total if it is.

There are also other ways that are a lot faster, but this is the simplest.

---

### Post by MONODA on 2008-08-18
> test whether it is divisible by 3 or 5 and only add it to the total if it is.
I thought of that at first then I realized that I didnt know how to do that.

> try replacing the line "print var" with "return var"
if I do that then it doesnt print the value of var at all.

> you haven't set the variables three and five.
how so? I have "three = multi(3)" and "five = multi(5)" how is that not setting the variables?

---

### Post by howlingmadhowie on 2008-08-18
three=multi(3) doesn't set the variable because multi doesn't return a value. try:

```
def multi(x): 
        var = 0
        add = 0
        for y in range(0, 1000, x):
                print y
                add += 3
                var += add
        print var
        return var
three = multi(3)
five = multi(5)
three
five
```

---

### Post by CptPicard on 2008-08-18
There is no "return" in your "multi" so therefore it returns "None" which is then stuck to those variables of yours.

---

### Post by meanburrito920 on 2008-08-18
% is the modulus operand. It gives the remainder of a division expression. so for example:

6 % 3 would give you 0, because there is a remainder of 0. If the remainder is 0, then the number is divisible by the other.

5 % 3 would give you 2, because the remainder of 5/3 is 2. Therefore 5 is not divisible by 3.

You can use this to minimize your program considerably.

---

### Post by Lster on 2008-08-18
[QUOTE=howlingmadhowie]three=multi(3) doesn't set the variable because multi doesn't return a value.[/QUOTE]

[QUOTE=CptPicard]There is no "return" in your "multi" so therefore it returns "None" which is then stuck to those variables of yours.[/QUOTE]

The code has two other errors apart from that. It's probably better to recode it using a simpler idea.

---

### Post by MONODA on 2008-08-18
Oh alright I get it, thanks. here is what I have know but Im still not getting the right answer:

[PHP]def multi(x): 
        var = 0
        add = 0
        for y in range(0, 1000, x):
                add += 3
                var += add
        return var
three = multi(3)
five = multi(5)
int(three)
int(five)
total = three + five
print total
[/PHP]

---

### Post by MONODA on 2008-08-18
> The code has two other errors apart from that. It's probably better to recode it using a simpler idea.
thanks for the advice, I'll get to working on that.

---

### Post by mike_g on 2008-08-18
Like lster said, you should only need two variables one for the loop and one for the total. In pseudocode:
```

total =0;

for count = 1 to 999
   if count%5 = 0 or count%3 = 0
      total += count
```

---

### Post by Lster on 2008-08-18
[QUOTE=Project Euler]Find the sum of all the multiples of 3 or 5 below 1000.[/QUOTE]

Two errors remain:

[PHP]for y in range(0, 1000, x):
	add += 3
	var += add[/PHP]

And the way you count multiples of three and multiples of five. Their sum is not the multiples of 3 and 5 as you have counted multiples of 15 twice.

---

### Post by howlingmadhowie on 2008-08-18
one problem is, you always add 3 to the total, so the chain of numbers you add for multi(3) is the same as for multi(5), just longer. by how much should you increment 'add' each time?

the next problem is more difficult, so i'll mention that later.

---

### Post by cprofitt on 2008-08-18
I did this originally in C# and the % operator was the key to my solution.

here is the Python code that I worked up

[php]
total = 0

for i in range(1,1000,1):
   if i%3==0 or i%5==0:
      total += i

print total
[/php]

---

### Post by MONODA on 2008-08-19
Last night I went ahead and started a new python script but today when I was messing around with it whenever I would test it, I would accidently test the old one so I kept getting the same answer no matter what lol. It took me a few minutes to realize my mistake. Anyway, here is what I wrote last night, thanks A LOT for your help; I learned a lot.

[PHP]total = 0       
for x in range(0, 1000):
        if x % 3 == 0 or x % 5 == 0: 
                total += x
        else:
                continue
print total
[/PHP]
It gave me the right answer :D Im off to question 2 :).

BTW if I were to put that code into a function, what is the line I would add at the end that would run the function (other than calling the function the normal func() way). Thanks you guys.

---

### Post by ghostdog74 on 2008-08-19
> **MONODA said:**
> 
[PHP]total = 0       
for x in range(0, 1000):
        if x % 3 == 0 or x % 5 == 0: 
                total += x
        else:
                continue
print total
[/PHP]


after you get the hang of Python, you will know that it gives you a lot of useful methods, such as sum()
```

sum([i for i in range(1,1001) if i % 3 == 0 or i % 5 == 0])

```

---

### Post by howlingmadhowie on 2008-08-19
using the % operator does yield the right answer. it is however pretty slow, since the % function takes a long time. can you think of a quicker way of doing this? hint: have a look [here]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes") and try to adapt it to your situation.

btw, as far as i know in python (or in most programming languages), the only way to call a function is to call it, so i'm not sure what you mean by "what is the line I would add at the end that would run the function (other than calling the function the normal func() way)". 

it's interesting to think about what a function actually is and different programming paradigms look at functions very differently. on the one hand you have the "functions are something special" school (languages like c and java) and then you have the "functions are just like other variables" school (scheme/lisp, smalltalk, javascript, etc.). python allows to some extent both approaches if you use the keyword lambda, but to the best of my knowledge it doesn't allow much more than very simple functions to be defined this way:

```

>>> def add_num(n):
...    return lambda x : n + x
...
>>> add_2_to=add_num(2)
>>> add_2_to(3)
5

```

it even has an ```
eval()
``` function, which can be a lot of fun:

```

>>> add_5_to=add_num(5)
>>> my_string="add_5_to"
>>> eval(my_string)(7)
12

```

note this still can be useful (try in c to automate the creation of 100 functions to add from 1 to 100 respectively to their argument!) but it's quite a way short of javascript/lisp/scheme/smalltalk etc.

of course, if you really want to see what functions can do, have a look at forth ;)

---

### Post by Def13b on 2008-08-19
There is also a linked PDF available once you've solved the problem. Unfortunately only available for a few of the earlier problems. They do however provide a great way to see other options on how to solve the problem in a efficient way.

---

### Post by dustman on 2008-08-19
interesting problem :-?

my Java code looks something like this:```

public class Test {
	
	public static void main(String args[]) {
		int sum = 0;
		for (int i=1;i<1000;i++) {
			if (i%3 == 0 || i%5 == 0) {
				sum = sum + i;
			}
		}
		System.out.println("Sum is:"+sum);
	}
}

```

---

### Post by Lster on 2008-08-19
[QUOTE=Def13b]There is also a linked PDF available once you've solved the problem. Unfortunately only available for a few of the earlier problems. They do however provide a great way to see other options on how to solve the problem in a efficient way.[/QUOTE]

Some of the later problems have PDFs for reference as well.

For anyone with interest in an efficient solution:

[PHP]
def rangediv(n, d):
	return n/d*(d+n-n%d)/2

n = 10**3-1
print rangediv(n, 3) + rangediv(n, 5) - rangediv(n, 15)
[/PHP]

It uses arithmetic sequences to evaluate the sum of sets of multiples...

---

### Post by MONODA on 2008-08-19
howlingmadhowie, I was talking about : ```
if __name__ == '__main__':
```

thanks for the help guys I will look into making my program more efficient.

---

### Post by NovaAesa on 2008-08-19
Here's the mathematical solution:

There are 999 numbers to be considered: 1 through to 999.

Consider multiples of three:
```
999 / 3 = 333
```
So there are 333 multiples of 3. They form the sequence:
```
{3, 6, 9, 12... 996, 999}
```
The sum of the equivalent series can be calculated as follows:
```
sum = (n/2)(a1 + an)
    = (333/2)(3 + 999)
    = 166833
```

Similarly for multiples of five:
```
999 / 5 = 199.8
```
So there are 199 multiples of 5 (you take the integer part). They form the sequence:
```
{5, 10, 15... 990, 995}
```
Their sum is as follows (same method as above):
```
sum = (n/2)(a1 + an)
    = (199/2)(5 + 995)
    = 99500
```

Similarly for multiples of fifteen:
```
999 / 15 = 66.6
```
So there are 66 multiples of 15 (you take the integer part). They form the sequence:
```
{15, 30, 45... 975, 990}
```
Their sum is as follows (same method as above):
```
sum = (n/2)(a1 + an)
    = (66/2)(15 + 990)
    = 33165
```

Now you just have to apply the inclusion/exclusion principal. It more or less says:
```
|A&#8746;B| = |A| + |B| - |A&#8745;B|
```

Now, if we let set A be the numbers divisible by 3 and set B be the numbers divisible by 5:
```
|A&#8746;B| = 166833 + 99500 - 33165
      = 233168
```


Now, I'm not sure if this is correct or not (I didn't check). But theoretically this should be the answer. It just goes to show that coding isn't always necessary :guitar:

---

### Post by Lster on 2008-08-19
[QUOTE=NovaAesa]Now, I'm not sure if this is correct or not (I didn't check).[/QUOTE]

Your working and answer are correct.

---

### Post by NovaAesa on 2008-08-19
Woooo! I win at maths!

---

### Post by howlingmadhowie on 2008-08-19
here's a fun answer which doesn't take too much time:

```
def findtotal():
  threes_runner=0
  fives_runner=0
  total=0

  while (True):
      if (threes_runner<fives_runner):
          threes_runner+=3
          if (threes_runner!=fives_runner and threes_runner<1000):
              total+=threes_runner
      else:
          fives_runner+=5
          if (fives_runner < 1000):
              total+=fives_runner
      if (fives_runner > 999 and threes_runner > 999): break

  return total


print findtotal()
```

---

### Post by NovaAesa on 2008-08-19
Here was my original solution (I did it about 4 months ago). Written in Java.

[php]
class SumMult35 {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i < 1000; i++) {
            if (i % 3 == 0 || i % 5 == 0) {
                sum += i;
            }
        }
        System.out.println(sum);
    } 
}
[/php]

---

### Post by Lster on 2008-08-19
Or:

[PHP]
n = 10**3
v = set([])

for a in xrange(0, 1000, 3): v.add(a)
for a in xrange(0, 1000, 5): v.add(a)

print sum(v)
[/PHP]

---

### Post by howlingmadhowie on 2008-08-20
> **NovaAesa said:**
> Here was my original solution (I did it about 4 months ago). Written in Java.

[php]
class SumMult35 {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i < 1000; i++) {
            if (i % 3 == 0 || i % 5 == 0) {
                sum += i;
            }
        }
        System.out.println(sum);
    } 
}
[/php]

the problem here is the modulus function. it's dog slow on most architectures. The solution with sets is of course ideal, but either requires support in the programming language or (preferably) an understanding of arrays.

---

### Post by sznurek on 2008-08-20
Why not like that:
[PHP]
print sum(set(range(3,1000,3) + range(5,1000,5)))
[/PHP]
?

---

### Post by Lster on 2008-08-20
That should work! :)

---

### Post by generalguy on 2008-08-20
That should work, but again, is very slow since you are iterating over a list. Plus it won't work in general ([x]range has an upper limit, 10**20 won't work, for example).

---

### Post by howlingmadhowie on 2008-08-21
> **generalguy said:**
> That should work, but again, is very slow since you are iterating over a list. Plus it won't work in general ([x]range has an upper limit, 10**20 won't work, for example).

i wonder how slow that is. one hopes that set(args) just calls a malloc(num(args) * sizeof *ptr).

oh hang on. numbers in python are objects to. oh, i see the problem. it may well have a clever hashing function to make checking for the presence of an object in a set a little faster, but we're still looking at O(n) for every insertion here. nasty. 

and this is, as you pointed out, horrible:

```
>>> set(range(1, 10**10))
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
OverflowError: range() result has too many items
```

---

### Post by benthebadger on 2008-08-21
I have been playing around with python 3. This is what I got for Project Euler Problem 1. Lster has been teaching me python.:)

[PHP]t = 0
for i in range(0, 1000):
    if i%3==0 or i%5==0:
        t = t + i

print(t)[/PHP]

---

### Post by y-lee on 2008-08-21
Of course the most efficient solution is simply

```
print 3*333*167 + 5*199*100 - 15*67*33
```

In case you are wonder how I came up with this consider the following somewhat more verbose yet equivalent version (in python):

```
def triangle(n):
    return n*(n + 1)/2
    
def euler1(m):
    m = m - 1
    return 3*triangle(m/3) + 5*triangle(m/5) - 15*triangle(m/15)
    
print euler1(1000)
```

If this is still not clear consider the fact that the sum of 1 to n is really the n*th* [triangle number]("http://en.wikipedia.org/wiki/Triangular_number"), which is what my **triangle **function above calculates. Now the sum of multiples of say 3 from 3 to 3*n is simply 3 times the n*th* triangle number by the [distributive principle ]("http://en.wikipedia.org/wiki/Distributivity"). 

Now in the problem *Find the sum of all the multiples of 3 or 5 below 1000*, we find the sum of the multiples of 3 add that to the sum of the multiples of 5. But since 3 and 5 both divide 15 we have added this twice so we then subtract the sum of the multiples of 15, hence 

```
3*triangle(m/3) + 5*triangle(m/5) - 15*triangle(m/15)
```

Which btw is really the equialvent to my first statement above:

```
3*333*167 + 5*199*100 - 15*67*33
```

---

### Post by generalguy on 2008-08-21
Yep. That's all. If you want to generalize it to a set of divisors D, then you must use the inclusion-exclusion principle.

[PHP]
from itertools import izip
import operator as op

def sdiv(k, n):
    max_div = n / k
    return (((max_div)*(max_div+1)) / 2) * k

def powerset(s):
    d = dict(izip
            ((1<<i for i in xrange(len(s))),
            (set([e]) for e in s)
            ))
    subset = set()
    for i in xrange(1, 1<<len(s)):
        subset = subset ^ d[i & -i]
        yield subset

def euler1(sd,n):
    pset = powerset(sd)
    sum = 0
    for ss in pset:
        sum_divs = sdiv(reduce(op.mul, ss),n-1)
        if len(ss) % 2 == 0:
            sum -= sum_divs
        else:
            sum += sum_divs
    return sum
        

pset = powerset([3,5])
facts = ( ((-1) ** ((len(ss) % 2) + 1)) * sdiv(reduce(op.mul, ss),1000-1) for ss in pset )
print sum(facts)
print euler1([3,5],1000)
[/PHP]

The powerset generator is not mine ( i modifed it a little; it also does not return the empty set); it works because you can use binary numbers to model inclusion of elements in a powerset.

---

### Post by y-lee on 2008-08-22
> **generalguy said:**
> Yep. That's all. If you want to generalize it to a set of divisors D, then you must use the inclusion-exclusion principle.

. . .

The powerset generator is not mine ( i modifed it a little; it also does not return the empty set); it works because you can use binary numbers to model inclusion of elements in a powerset.

Very Impressive code generalguy :)

---

