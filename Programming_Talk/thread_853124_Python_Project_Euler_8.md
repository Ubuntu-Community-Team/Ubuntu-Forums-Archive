---
title: "Python: Project Euler 8"
date: 2008-07-08
forum: Programming Talk
---

### Post by spadewarrior on 2008-07-08
Hello. I'm trying out some of the Euler problems in an attempt to learn Python. Here's the problem:

[http://projecteuler.net/index.php?section=problems&id=8](http://projecteuler.net/index.php?section=problems&id=8)

And here's my code:

[PHP]string = # that really long number, edited out for page-width-sanity

num = []

for char in string:
	num.append(int(char))


answers = []


i = 0

while i <= len(num) - 5:
	k = i + 1
	l = i + 2
	m = i + 3
	n = i + 4
	prod = ( num[i] * num[k] * num[l] * num[m] * num[n])
	answers.append(prod)
	i += 1

print max(answers)[/PHP]


I get the correct answer but the code is clunky and I'm pretty sure there are some built-in python functions that would make this a lot easier to write, more memory efficient and easier on the eye. 

What nice functions am I missing out on here?

---

### Post by ghostdog74 on 2008-07-08
```

import sys,textwrap
def mul(x,y): return x*y
string = """731671........"""
num = []
n=textwrap.wrap(string,5)
for i in n: num.append(reduce(mul,map(int,list(i))))
print max(num)

```

---

### Post by Martin Witte on 2008-07-08
If I use ghostdogs code I get the wrong answer. Building on his code I have
[PHP]
#!/usr/bin/env python
string = '7316717...'

i = 0
max = 0
while i < len(string) - 4:
    prod = reduce(lambda x,y: x*y, map(int, string[i:i+5]))
    if prod > max:
        max = prod
    i+= 1
print max[/PHP]

textwrap (see [the docs]("http://docs.python.org/lib/module-textwrap.html")) chops a string into pieces of equal length, here you need to advance through the string 5 digits each

---

### Post by nanotube on 2008-07-08
> **ghostdog74 said:**
> ```

import sys,textwrap
def mul(x,y): return x*y
string = """731671........"""
num = []
n=textwrap.wrap(string,5)
for i in n: num.append(reduce(mul,map(int,list(i))))
print max(num)

```

ghostdog, your solution is not correct, as it doesn't try /all/ consecutive 5-digit numbers, but only non-overlapping sequences thereof. in the case of, eg, a 10-digit string, you have only two products, of digits 1-5, and of digits 6-10. however, the problem asks to check product of digits 1-5, digits 2-6, digits 3-7, etc.

despite that, thanks for introducing me to the textwrap module - i didn't even know that was there. :)

---

### Post by ghostdog74 on 2008-07-08
A case of misreading the problem requirement. My bad.

---

### Post by ghostdog74 on 2008-07-08
> **nanotube said:**
> 
i didn't even know that was there. :)
if you master [this](http://docs.python.org/lib/), you are invincible.

---

### Post by Martin Witte on 2008-07-08
if you prefer compact code you can use a [list comprehension]("http://docs.python.org/tut/node7.html#SECTION007140000000000000000"):
```

big_number = '731671765313....'
print max([ reduce(lambda x,y: x*y, map(int, big_number[i:i+5])) for i in range(0, len(big_number) -4) ])

```

---

### Post by nanotube on 2008-07-08
> **ghostdog74 said:**
> if you master [this](http://docs.python.org/lib/), you are invincible.

as long as you don't misread problem requirements, that is. ;) :popcorn:

---

### Post by rye_ on 2008-07-08
hmmm.... I had a go at this just to try to outsmart you all with the shortest code.... Things didn't go to plan.

[PHP]
array = "73167176531330624919225119674426574742355349194934
96983520312774506326239578318016984801869478851843
85861560789112949495459501737958331952853208805511
12540698747158523863050715693290963295227443043557
66896648950445244523161731856403098711121722383113
62229893423380308135336276614282806444486645238749
30358907296290491560440772390713810515859307960866
70172427121883998797908792274921901699720888093776
65727333001053367881220235421809751254540594752243
52584907711670556013604839586446706324415722155397
53697817977846174064955149290862569321978468622482
83972241375657056057490261407972968652414535100474
82166370484403199890008895243450658541227588666881
16427171479924442928230863465674813919123162824586
17866458359124566529476545682848912883142607690042
24219022671055626321111109370544217506941658960408
07198403850962455444362981230987879927244284909188
84580156166097919133875499200524063689912560717606
05886116467109405077541002256983155200055935729725
71636269561882670428252483600823257530420752963450"

class Array
	def product	
		return self.inject() {|x,j| j*=x}		
	end
end	

j = 0
a = array.split(/\n/).join("").split(//).collect {|x| x.to_i}
(0..a.length-5).each { |x| j = [a[x,5].product, j].max } 
p j

[/PHP]

---

