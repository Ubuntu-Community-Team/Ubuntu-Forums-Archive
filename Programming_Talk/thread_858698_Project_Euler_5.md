---
title: "Project Euler 5"
date: 2008-07-13
forum: Programming Talk
---

### Post by tiachopvutru on 2008-07-13
Well, this is only part of what I try to do to solve Project Euler 5. Even if I'm on a wrong stop, it would be helpful to know why my function doesn't do what I want it to do:

```
#this function makes sure that no single item in a list is a divisor of another
#item in the same list.
def slim_down(L):
    reversedL = reversed(L[:])
    for each in reversedL:
        for another in reversedL:
            if each % another == 0 and not each == another:
                try:
                    L.remove(another)
                except ValueError:
                    pass
                    
    return L

question = range(1, 21)
print slim_down(question)

```

What I'm trying to do with the function is there on the comment. The result I get is:
```
[3, 6, 7, 8, 9, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20]
```
when it should have only be [11, 12, 13, 14, 15, 16, 17, 18, 19, 20]

Although, on second thought... I think I'm better off just cut the list down into two equal halves, and take the latter half...

---

### Post by Def13b on 2008-07-13
I think the problem is this line:

reversedL = reversed(L[:])

reversed() returns a iterator and not a list. As you move into the body of your function you take the first item from the iterator (20) and check it against each other item (19-1), after it checks the (1) it raises StopInteration and your function exits returning L thats only been checked with 20.

Instead of reversed() if you make a straight copy of your list and use the reverse method on it you should get the result your after.

---

### Post by tiachopvutru on 2008-07-14
You are right... and I thought reversed(arg) returns a list, too... I also find that *for each in L[::-1] *works just as well.

Anyway, I ended up not using that slim_down function since it looks like it's going to run pretty slow, but I managed to complete Euler 5 anyway (well, it worked when I tested on range(1, 11), not sure about on range(1,21)).

Here's my code

[PHP]def lcm(arg):
    arg.sort()
    commonMult = reduce((lambda x, y: x * y), arg)  #multiply all numbers
    answer = temp = arg[-1]
    mult = 1
    last = len(arg) - 1

    #this loop continues until the multiple of the largest element equals the
    #common multiple of all numbers in the arg argument unless it finds the
    #lowest common denominator
    while answer <= commonMult:
        answer *= mult
        while answer % arg[last] == 0:
            last -= 1
            if last == -1:
                return answer
        else:
            last = len(arg) -1
        answer /= mult
        mult += 1
        

question = range(1, 21)
print lcm(question)
[/PHP]

It runs rather slow, though. When I googled for Project Euler 5 to check my solution, I found that the [first comment on a blog]("http://timjoh.com/project-euler-5-find-the-lowest-common-multiple/") provides hint for optimization, so I think I'm going to try that next. :)

---

### Post by jim_24601 on 2008-07-14
re the blog link: He came up with a script that takes *20 minutes* to get the answer? What's he running it on, an abacus? I did it in 5 ... *without* a computer.

---

### Post by bcl1713 on 2008-07-14
```
#2520 is the smallest number that can be divided by each of the 
#numbers from 1 to 10 without any remainder.

#What is the smallest number that is evenly divisible by all of the 
#numbers from 1 to 20?

def gcd(a, b):
	if b == 0:
		return a
	return gcd(b, a % b)

def lcm(a, b):
	return a * b / gcd(a, b)

print lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(1, 2),3),4),5),6),7),8),9),10),11),12),13),14),15),16),17),18),19),20)
```

The last line could be cleaned up quite a bit.. but solves in milliseconds. :)

---

### Post by jim_24601 on 2008-07-14
Doesn't that print 20! and not the answer to the puzzle, though? Not that I've run it. I've yet to come up with something better than O(n^2).

edit: Actually I think I've got it down to n log n, but it's not quite trivial to get the complexity for my current solution.

---

### Post by Lux Perpetua on 2008-07-14
> **jim_24601 said:**
> Doesn't that print 20! and not the answer to the puzzle, though? Not that I've run it. No, it gives the correct answer. 20! is 1*2*3* ... * 20, not LCM(1, 2, 3, ..., 20). (I did just run it, and it agrees with the number I computed by hand.)

edit: The best algorithm I have has complexity O(N^2), and that includes the complexity of integer arithmetic. If you ignore the complexity of integer arithmetic (i. e., assume all basic operations are O(1)), then it becomes O(N).

---

### Post by jim_24601 on 2008-07-14
My apologies. I misread your solution; it is indeed correct.

I started with a list of numbers from 2 to 20 and the LCM set to 1. For each number x in the list, I multiplied the LCM by x, and divided all subsequent numbers in the list that were divisible by x, by x. I think that comes out to n log n if you skip multipliers that have been divided down to 1.

---

### Post by Lux Perpetua on 2008-07-15
My O(N^2) (or O(N), depending on your perspective) solution is first to find all the primes up to N (O(N), using a careful sieve of Eratosthenes), then for each prime, to find its highest power that doesn't exceed N (O(N/log(N)) (**edit**: actually, this step appears to be O(N*log(log(N))/log(N)) in my algorithm (see my next post below)), since there are O(N/log(N)) primes not greater than N), and then to multiply all those prime powers together (also O(N/log(N))). Stated that way, finding the primes dominates the running time, but if you include the complexity of multiplying large numbers, my estimate becomes dominated by the last step and goes up to O(N^2).

---

### Post by tiachopvutru on 2008-07-15
> **bcl1713 said:**
> ```
#2520 is the smallest number that can be divided by each of the 
#numbers from 1 to 10 without any remainder.

#What is the smallest number that is evenly divisible by all of the 
#numbers from 1 to 20?

def gcd(a, b):
	if b == 0:
		return a
	return gcd(b, a % b)

def lcm(a, b):
	return a * b / gcd(a, b)

print lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(lcm(1, 2),3),4),5),6),7),8),9),10),11),12),13),14),15),16),17),18),19),20)
```

The last line could be cleaned up quite a bit.. but solves in milliseconds. :)

That's so awesome. It's straightforward and yet not-so-straightforward at the same time :). Anyway, after looking at that, I gave up trying to optimize my first solution. I rewrote what you did into function, though...

```
def gcd(a, b):
    if b == 0:
	    return a
    return gcd(b, a % b)

def lcm(*args):
    a, i = args[0], 1
    while i < len(args):
        a = a * args[i] / gcd(a, args[i])
        i += 1
    return a

print lcm(*range(1, 21))
```

Changing range(1, 21) to xrange(1, 21) also works, although I don't know why it does.

---

### Post by jim_24601 on 2008-07-15
> **Lux Perpetua said:**
> My O(N^2) (or O(N), depending on your perspective) solution is first to find all the primes up to N (O(N), using a careful sieve of Eratosthenes),

O(N) sieve of Eratosthenes? How does that work?

> then for each prime, to find its highest power that doesn't exceed N (O(N/log(N)), since there are O(N/log(N)) primes not greater than N),

Surely finding the highest power that doesn't exceed N is itself O(log N), so this step is really O(N)?

> but if you include the complexity of multiplying large numbers, my estimate becomes dominated by the last step and goes up to O(N^2).

I wasn't considering the complexity of multiplying, no.

I came up, independently, with the following in C++.
```
  long lcm = 1;
  long factors [21];
  for (long i = 2; i <= 20; ++i)
  {
    factors [i] = i;
  }
  for (long i = 2; i <= 20; ++i)
  {
    if (factors[i] != 1)
    {
      long power = factors[i];
      while (power <= 20)
      {
	power *= factors[i];
	lcm *= factors[i];
      }
      for (long j = 2*factors[i]; j <= 20; j += factors[i])
      {
	factors[j] = 1;
      }
    }
  }
  cout << lcm << '\n';
```

It's basically what you describe.

---

### Post by jespdj on 2008-07-15
Here's my solution to Euler problem 5 in Ruby. It takes a fraction of a second to find the answer.
```
#!/usr/bin/env ruby

@primes = [2, 3, 5, 7, 11, 13, 17, 19]

def factorize(n)
  factors = []
  while n > 1
    f = @primes.find(n) {|p| n % p == 0 }; factors << f; n /= f
  end
  return factors
end

counts = [0] * 8

(2..20).each do |n|
  factors = factorize(n)
  @primes.each do |p|
    cnt = factors.select {|i| i == p }.length
    counts[@primes.index(p)] = cnt if counts[@primes.index(p)] < cnt
  end
end

result = 1
(0..7).each {|i| result *= @primes[i] ** counts[i] }

puts "Answer: #{result}"

```

---

### Post by bcl1713 on 2008-07-15
> **tiachopvutru said:**
> That's so awesome. It's straightforward and yet not-so-straightforward at the same time :). Anyway, after looking at that, I gave up trying to optimize my first solution. I rewrote what you did into function, though...

```
def gcd(a, b):
    if b == 0:
	    return a
    return gcd(b, a % b)

def lcm(*args):
    a, i = args[0], 1
    while i < len(args):
        a = a * args[i] / gcd(a, args[i])
        i += 1
    return a

print lcm(*range(1, 21))
```

Changing range(1, 21) to xrange(1, 21) also works, although I don't know why it does.

There would be the cleanup I was refering to.. Though I probably would have done a recursive call to the function with one fewer argument until there were two.

---

### Post by Lux Perpetua on 2008-07-15
> **jim_24601 said:**
> O(N) sieve of Eratosthenes? How does that work?You need to make sure you visit each composite number exactly one time, not once for each of its prime factors. To do this, you can't visit every multiple of a given prime; you need to make sure you only visit those multiples that are not divisible by smaller primes (because they were already crossed off). But at this stage of the sieve of Eratosthenes, you know which numbers are not divisible by smaller primes, which are exactly the numbers you need to multiply your current prime by. Using that information efficiently enough to visit every number you need to visit in O(1) time is a matter of finding a suitable data structure. 

> Surely finding the highest power that doesn't exceed N is itself O(log N), so this step is really O(N)?Actually, you can do it in O(log(log(N))) amortized time per prime by iterating over your primes p from largest to smallest and maintaining the smallest value of t such that p^t > N and incrementing t as needed. You will only need to increment t O(log(N)) times because t is only incremented when you cross N^(1/k) for some integer k, and there are only about log_2(N) such values that are greater than 2. There are actually only O(N/log(N)) primes less than N, and it only takes O(log(t)) multiplications to compute p^t, and t itself never exceeds 1 + log_2(N), so this step is actually O(N*log(log(N))/log(N) + log(N)) = O(N*log(log(N))/log(N)), which is o(N).

---

