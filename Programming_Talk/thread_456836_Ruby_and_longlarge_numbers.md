---
title: "Ruby and long/large numbers"
date: 2007-05-28
forum: Programming Talk
---

### Post by DucentiVigintiDuo on 2007-05-28
Hey everyone,

this might sound like a stupid question, but what can one do to handle extremely long numbers in Ruby? I've recently started solving the problems in the Euler project, and even though I think I've got the solution to a certain problem, it doesn't seem to work.

Computing (factoring in particular) with the number 317584931803 seems to work just fine, but later down in the code when I ask it to do that many repetitions it gets stuck!

Is that because my computer doesn't have enough processing power or is it Ruby's fault?

I'm on a 1.83 Dual Core Macbook with 512MB of RAM.

And here's the code fragment:

```
factors = []
x = 2
number = 317584931803

begin
   if(number%x==0)
   factors << x
   end   
   x+=1
   end until x > number


puts factors
```

---

### Post by nitro_n2o on 2007-05-28
That sounds like iterating forever!!! 
I'm not a ruby expert but try: 
end until x*x < number
there are no prime factors greater than the sqrt of the number

---

### Post by DeadEyes on 2007-05-28
Ruby should handle big numbers automatically, as far as i know it hold numbers in a knid of string so the only limit is memory. no int type overflows.

---

### Post by DucentiVigintiDuo on 2007-05-28
> **nitro_n2o said:**
> That sounds like iterating forever!!! 
I'm not a ruby expert but try: 
end until x*x < number
there are no prime factors greater than the sqrt of the number

I thought of doing that but I didn't remember if it was mathematically right.
Thanks nitro, I'm going to try it out and see if it works now.

EDIT: I tried out x*x > number (it's > and not < because it continues until the number is bigger than that, not while it is smaller)
but then I thought x > Math.sqrt(number) was more elegant and gave the same result and preferred to keep it that way.

And just for the heck of it,
here's the problem:

> The prime factors of 13195 are 5, 7, 13 and 29.

What is the largest prime factor of the number 317584931803?


And here is my solution using Ruby:

```
factors = []
primes = []
nonprimes = []
largest = 0
x = 2
number = 317584931803

begin
   if(number%x==0)
   factors << x
   end   
   x+=1
   end until x > Math.sqrt(number)

puts factors

for i in factors
    for x in 2...i
       if((i%x==0)&&(nonprimes.index(i)==nil))
             nonprimes << i
             puts "#{i.to_s} is a non-prime factor"
       end
    end
end

primes = factors - nonprimes
puts primes

largest = primes.max

puts "The largest prime factor of 317584931803 is #{largest.to_s}"
```

---

### Post by nitro_n2o on 2007-05-28
well that work! I'm starting the Euler project and I have just used your answer :$ i'm not a good ruby programmer.. however, for faster code you can get the largest prime factor by finding all primes less than the sqrt root of that number and the last factor you find must be the largest.. just an idea!! and yeah euler's project looks interesting :)

---

### Post by Mathiasdm on 2007-05-28
Ah, I just saw the answer when looking through the forums of problems I've solved :p
It's way too addictive!

---

### Post by DucentiVigintiDuo on 2007-05-28
> **nitro_n2o said:**
> well that work! I'm starting the Euler project and I have just used your answer :$ i'm not a good ruby programmer.. however, for faster code you can get the largest prime factor by finding all primes less than the sqrt root of that number and the last factor you find must be the largest.. just an idea!! and yeah euler's project looks interesting :)

That *is* what I'm doing, except I think it's actually easier to do "array.max" rather than find the last element. And I wasn't aware of the Prime class either, so I had to figure out if the numbers were prime numbers myself. I'm gonna try and use that class for the next problem though. :)

---

