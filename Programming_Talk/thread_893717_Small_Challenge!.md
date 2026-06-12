---
title: "Small Challenge!"
date: 2008-08-18
forum: Programming Talk
---

### Post by Lster on 2008-08-18
Just looking at Project Euler problem 1 again recently, I've had an idea for a small challenge which is essentially an extension of it. For reference, here is the first Project Euler:

[http://projecteuler.net/index.php?section=problems&id=1](http://projecteuler.net/index.php?section=problems&id=1)

The new challenge is simply:

> Find the sum of all the multiples of 6, 13, 14, 22 or 77 below 10^20.

The answer is 40 digits long so big integers will be required! Post the answer in this thread and of course discussion is welcome. In fact, I may as well post this link now:

[http://en.wikipedia.org/wiki/Inclusion-exclusion_principle](http://en.wikipedia.org/wiki/Inclusion-exclusion_principle)

I was very fortunate to be pointed in this direction a while ago by Lux Perpetua. Thanks. ;)

---

### Post by jimi_hendrix on 2008-08-18
the link you give is to a different challenge...the sum off all multiples of three and five...

EDIT: sorry miss read :)

---

### Post by fifth on 2008-08-18
> **jimi_hendrix said:**
> the link you give is to a different challenge...the sum off all multiples of three and five...

[QUOTE=Lster] ... I've had an idea for a small challenge which is essentially an **extension** of it[/QUOTE]

:lolflag:

[edit]

I gave up looping to 10^20, was going to take a long time :(. I assume there's a better solution using the maths link given (or was that just for the comparison/result set?, didn't read much of the wiki)

---

### Post by Jessehk on 2008-08-18
My answer is 42 digits long, but I'm really not sure if it's correct or not (in terms of logic).

EDIT: here's the answer. Like I said, I doubt it's right. :)

186646686646686646685353313353313353313764

---

### Post by WW on 2008-08-18
> **Jessehk said:**
> My answer is 42 digits long, but I'm really not sure if it's correct or not (in terms of logic).

EDIT: here's the answer. Like I said, I doubt it's right. :)

186646686646686646685353313353313353313764

Your doubts are justified.  The sum of *all* the positive integers up to 10^20 is only 40 digits, so there is no way a 42 digit answer can be correct. :(

---

### Post by Jessehk on 2008-08-18
Aha!

I misread the limit to be 10E20, not 10^20.
I'm still not sure if the logic is correct, but here's my revised answer:

1866466866466866466833533133533133533169

---

### Post by meanburrito920 on 2008-08-19
I gave up after I realized my program was going to take into next year to finish. I'm interested in how it is done though(that is, if there is algorithm for it. For all I know the only way to solve it may be just a recursive loop, which is what I tried.)

So can whoever gets it please post their code?

---

### Post by NovaAesa on 2008-08-19
Hint: use the inclusion exclusion principal. You can do this problem with a calulator if it has enough decimal places. When I took discrete mathematics last semester, we did lots of problems like this.

---

### Post by Lster on 2008-08-19
None of the proposed answers match my own...

[QUOTE=NovaAesa]Hint: use the inclusion exclusion principal. You can do this problem with a calulator if it has enough decimal places. When I took discrete mathematics last semester, we did lots of problems like this.[/QUOTE]

That would be a little long winded, but quite possible. ;)

---

### Post by jimi_hendrix on 2008-08-19
is it possible with just loops...that formula from wikipedia is confusing

---

### Post by nvteighen on 2008-08-19
It smells like a job for a functional language. I'll give it a try on Scheme, but I don't guarrantee to have something too soon.

---

### Post by Lster on 2008-08-19
You'll need to know how to sum an arithmetic progression. And need to know the inclusion-exclusion principle so you know what to do... Of course, there could be other ways - I can't think of any!

I'll post my solution later if no one else is still attempting it then!

---

### Post by Lster on 2008-08-19
Here be the solution - don't peek if you're still trying to complete it!

[PHP]
# Copyright Lster, 2008

# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.


def gcd(a, b):
	while b != 0:
		t = b
		b = a%b
		a = t
	
	return a

def lcm(arr):
	g = 1
	for a in arr:
		g *= a/gcd(a, g)
	
	return g

def sdiv(n, d):
	return n/d*(d+n-n%d)/2

def sumto(n, ds):
	l = len(ds)
	
	arr = []
	for i in xrange(1, 2**l):
		j = i
		k = 0
		x = []
		while j > 0:
			if j%2 == 1: x += [ds[k]]
			k += 1
			j /= 2
		
		arr += [x]
	
	total = 0
	for a in arr:
		g = lcm(a)
		l = len(a)+1
		total += (-1)**l*sdiv(n, g)
	
	return total


#Set data
n = 10**20-1
d = [6, 13, 14, 22, 77]

#Fast inclusion-exclusion principle
print sumto(n, d)


#Check!
if n > 10**5:
	print "Too high to check!"
	exit()

total = 0
for i in xrange(1, n+1):
	for a in d:
		if i%a == 0:
			total += i
			break

print total

[/PHP]

As can be seen, the function sumto does most of the work. sdiv(n, d) gives the sum of all numbers less than or equal to n and divisible by d. The sumto works out all the possible groups and their signs and sums it all...

Of course, if there are k divisors, there are 2^k-1 sets... so the algorithm gets quite slow with many sets quickly.

---

### Post by mssever on 2008-08-19
> **jimi_hendrix said:**
> is it possible with just loops...that formula from wikipedia is confusing
It's possible, but suboptimal. That's the approach I've taken since my math skills are insufficient to understand the Wikipedia link (thanks, Lster, for posting code--it's a lot easier to understand than standard mathematical notation). Here's my code: ```
#!/usr/bin/env ruby

LIMIT = 10 ** 20
$stderr.puts "Limit: #{LIMIT}"
sum = 0

6.upto(LIMIT) do |i|
  if (i % 6 == 0 ||
      i % 13 == 0 ||
      i % 14 == 0 ||
      i % 22 == 0 ||
      i % 77 == 0)
    sum += i
  end
  $stderr.puts "#{i} of #{LIMIT}: #{sum}" if i % 100_000 == 0
end

puts sum
```I'm sure it works, but I don't have the answer yet. This approach is very slow. So far, I estimate that my program is a little under halfway to the solution, and it's used 17 hours 13 minutes of CPU time (and probably 18 or 19 hours of wall clock time). Since it's been running for so long, I refuse to stop it, but it's a suboptimal approach.

@Lster: How long should it take to find the answer with a decent algorithm?

---

### Post by generalguy on 2008-08-19
It shouldn't take very long, since the algorithm is dependent most on how fast you can enumerate subsets. (Which is exponential but there should be only 32).
This is my solution. I think it is correct (it gets a 40 digit number though).

[PHP]
from itertools import izip
import operator as op

def sdiv(k, n=10**20):
    max_div = n / k
    return (((max_div) *(max_div+1)) / 2) * k

def powerset(s):
    d = dict(izip(
            (1<<i for i in range(len(s))),
            (set([e]) for e in s)
            ))
    subset = set()
    for i in xrange(1, 1<<len(s)):
        subset = subset ^ d[i & -i]
        yield subset
        
pset = powerset([14, 22, 13, 6, 77])
facts = ( ((-1) ** ((len(ss) % 2) + 1)) * sdiv(reduce(op.mul, ss)) for ss in pset )
print sum(facts)
[/PHP]

This powerset generator is not mine, but I used it for a few other projects. In any case, it works on the principle that a binary number can model the inclusion of elements in a set.

---

### Post by dmm1285 on 2008-08-20
```

def multiple(factor, seq):
    for i in seq:
        if i % factor == 0:
            yield i
        else:
            pass

def multiple_of_6(seq):
    return multiple(6, seq)

def multiple_of_13(seq):
    return multiple(13, seq)

def multiple_of_14(seq):
    return multiple(14, seq)

def multiple_of_22(seq):
    return multiple(22, seq)

def multiple_of_77(seq):
    return multiple(77, seq)


def less_than_1E20(seq):
    for i in seq:
        if i < 10**20:
            yield i

def sequence():
    i = 0
    while True:
        yield i
        i = i + 1

def generator_sum(seq):
    sum = 0
    for i in seq:
        sum = sum + i
    return sum

a = sequence()
b = less_than_1E20(a)
c = multiple_of_13(b)
d = multiple_of_14(c)
e = multiple_of_22(d)
f = multiple_of_77(e)

total = generator_sum(f)
print total

```

Without looking at the wiki link at all, this is how I would implement it. What is the pythonic way of applying a lot of filters to a sequence? I feel like there is a cleaner way than I did it (though I usually use more descriptive variable names).

---

### Post by ghostdog74 on 2008-08-20
> **mssever said:**
> ```
#!/usr/bin/env ruby

LIMIT = 10 ** 20
$stderr.puts "Limit: #{LIMIT}"
sum = 0

6.upto(LIMIT) do |i|
  if (i % 6 == 0 ||
      i % 13 == 0 ||
      i % 14 == 0 ||
      i % 22 == 0 ||
      i % 77 == 0)
    sum += i
  end
  $stderr.puts "#{i} of #{LIMIT}: #{sum}" if i % 100_000 == 0
end

using your approach, i recoded in awk and changed MAX to 10000000
[code]
awk 'BEGIN {
 MAX=10000000
 for(i=1;i<MAX;i++ ) {
    if (    (i %  6 == 0 ) ||
            (i % 13 == 0) ||
            (i % 14 == 0) || 
            (i % 22 == 0) ||
            (i % 77 == 0)  ){
        total+=i
    }
 }
 printf "%d",total }' 
```

running both against the time command for 3 times,
```

# time ./test.rb
15234749765241

real    0m35.317s
user    0m35.306s
sys     0m0.004s
# time ./testawk.sh
15234749765241
real    0m20.143s
user    0m20.133s
sys     0m0.004s
# time ./test.rb
15234749765241

real    0m36.528s
user    0m36.502s
sys     0m0.004s
# time ./testawk.sh
15234749765241
real    0m19.291s
user    0m19.281s
sys     0m0.012s
# time ./test.rb
15234749765241

real    0m35.952s
user    0m35.946s
sys     0m0.008s
# time ./testawk.sh
15234749765241
real    0m20.533s
user    0m20.449s
sys     0m0.020s


```
I am not sure if i need to change anything else besides the 10^20 in the ruby script though.

---

### Post by nvteighen on 2008-08-20
It should be very easy in Python by using two queue lists and a functional approach. I mean:
1. Generate all numbers up to 10^20
2. filter() multiples and store them in a target list if they're not in "used" list.
3. Put the last included in "used".
4. When we reach 10^20, reduce() the target list using sum.

No need for an explicit inclusion-exclusion principle; you just leave it implicit by using the "used" list. This is programming, not formal maths ;)

EDIT: Maybe later I write this in code. Today I'm a bit busy.

---

### Post by Lster on 2008-08-20
> **mssever]@Lster: How long should it take to find the answer with a decent algorithm?[/QUOTE]

My algorithm takes way less than a second in Python (which is pretty slow). So it should run quickly on just about any language.

[QUOTE=nvteighen]1. Generate all numbers up to 10^20
2. filter() multiples and store them in a target list if they're not in "used" list.
3. Put the last included in "used".
4. When we reach 10^20, reduce() the target list using sum.[/QUOTE]

That algorithm will not work. The computational complexity of the algorithm is O(n)... so even on the assumption that you can check 10^9 numbers a second, it would take about 3171 years... The whole point of the challenge is you can't do things like that.  said:**
> This is programming, not formal maths ;)

Programming, alone, is to my knowledge incapable of completing this challenge.

---

### Post by nvteighen on 2008-08-20
> **Lster said:**
> 
That algorithm will not work. The computational complexity of the algorithm is O(n)... so even on the assumption that you can check 10^9 numbers a second, it would take about 3171 years... The whole point of the challenge is you can't do things like that. ;)

I see. I tried it after reading your post and I almost destroyed my swap partition. I retreat gracefully... ;)

Honestly, I like generalguy's more than yours. Your code is a mess, by the way...

---

### Post by Lster on 2008-08-20
Nah. It's just in another style to his. :)

---

### Post by mssever on 2008-08-20
> **ghostdog74 said:**
> running both against the time command for 3 times,
...
I am not sure if i need to change anything else besides the 10^20 in the ruby script though.You correctly modified the Ruby script. I knew that the Ruby interpreter is a bit slow, but it appears that in this situation, Ruby's comparative slowness is quite significant.

> **Lster said:**
> My algorithm takes way less than a second in Python (which is pretty slow). So it should run quickly on just about any language.
Ruby is slower than Python, but still, my approach is definitely bad.

---

### Post by generalguy on 2008-08-20
This can be done without any programming, although it is pretty tedious. The inclusion-exclusion link, although complex, gives it away.

---

### Post by Lster on 2008-08-20
Yes. And that's computers' use I guess: doing stuff we tell them, faster.

---

### Post by dmm1285 on 2008-08-20
Here is a more python implementation of my first version:
```

def multiple(factor, seq):
    for i in seq:
        if i % factor == 0:
            yield i
        else:
            pass

def multiple_of_6(seq):
    return multiple(6, seq)

def multiple_of_13(seq):
    return multiple(13, seq)

def multiple_of_14(seq):
    return multiple(14, seq)

def multiple_of_22(seq):
    return multiple(22, seq)

def multiple_of_77(seq):
    return multiple(77, seq)


def less_than_1E20(value):
    if value < 10**20:
        return True
    else:
        return False

def sequence():
    i = 0
    while True:
        yield i
        i = i + 1

def apply(seq, filters):
        for function in filters:
            seq = function(seq)
        return seq

def take_while(seq, predicate):
    for i in seq:
        if predicate(i) == True:
            yield i
        else:
            break

multiplicity_filters = [multiple_of_6,
                        multiple_of_13,
                        multiple_of_14,
                        multiple_of_22,
                        multiple_of_77]

filtered_sequence = apply(sequence(), multiplicity_filters)
total = sum(take_while(filtered_sequence, less_than_1E20))

print total


```
Here is what I got from the wiki:
If we find the LCM of all of our multiples, then multiply that by the cardinality of the union of all of our sets, then sum that, we would have our answer?

---

### Post by generalguy on 2008-08-20
> **dmm1285 said:**
> Here is a more python implementation of my first version:
```

def multiple(factor, seq):
    for i in seq:
        if i % factor == 0:
            yield i
        else:
            pass

def multiple_of_6(seq):
    return multiple(6, seq)

def multiple_of_13(seq):
    return multiple(13, seq)

def multiple_of_14(seq):
    return multiple(14, seq)

def multiple_of_22(seq):
    return multiple(22, seq)

def multiple_of_77(seq):
    return multiple(77, seq)


def less_than_1E20(value):
    if value < 10**20:
        return True
    else:
        return False

def sequence():
    i = 0
    while True:
        yield i
        i = i + 1

def apply(seq, filters):
        for function in filters:
            seq = function(seq)
        return seq

def take_while(seq, predicate):
    for i in seq:
        if predicate(i) == True:
            yield i
        else:
            break

multiplicity_filters = [multiple_of_6,
                        multiple_of_13,
                        multiple_of_14,
                        multiple_of_22,
                        multiple_of_77]

filtered_sequence = apply(sequence(), multiplicity_filters)
total = sum(take_while(filtered_sequence, less_than_1E20))

print total


```
Here is what I got from the wiki:
If we find the LCM of all of our multiples, then multiply that by the cardinality of the union of all of our sets, then sum that, we would have our answer?

Try doing this for smaller numbers first. You shouldn't be doing any iterating up to 10**20 at all. Secondly, 

[PHP]
def less_than_1E20(value):
    if value < 10**20:
        return True
    else:
        return False
[/PHP]

is not pythonic. If you truly want to iterate up to 10**20, you should look into the itertools module. What you are doing is, basically mssever's and ghostdog's, except much slower and more obfuscated. Think about the mathematics first. 

For example:

Suppose we want to find the sum of the numbers that are multiples of 3 and 5 under 20.

They are: 3,5,6,9,10,12,15,18

Numbers that are multiples of 3:

sum(3,6,9,12,15,18 ) = 3 * (sum(1,2,3,4,5,6))

Numbers that are multiples of 5:

sum(5,10,15) = 5 * (sum(1,2,3))

Suppose we add sum(5,10,15)  + sum(3,6,9,12,15,18 )? Would we get the correct answer?

---

### Post by dmm1285 on 2008-08-20
> 
Suppose we want to find the sum of the numbers that are multiples of 3 or 5 under 20.

They are: 3,5,6,9,10,12,15,18

Numbers that are multiples of 3:

sum(3,6,9,12,15,18 ) = 3 * (sum(1,2,3,4,5,6))

Numbers that are multiples of 5:

sum(5,10,15) = 5 * (sum(1,2,3))

Suppose we add sum(5,10,15)  + sum(3,6,9,12,15,18 )? Would we get the correct answer?

I misread the original problem. I thought that it said muliples of n and m, not n or m. In that case, my solution is completely incorrect.

---

