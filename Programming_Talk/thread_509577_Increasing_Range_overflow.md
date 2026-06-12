---
title: "Increasing Range overflow?"
date: 2007-07-25
forum: Programming Talk
---

### Post by flummoxed on 2007-07-25
I want to get python to determine the range of a 12-digit number. When I try the command:

```
range(317584931803)
```

I get this error code:

```
Traceback (most recent call last):
  File "C:/Python25/isPrime3.py", line 26, in <module>
    checkPrime = range(mainNum)
OverflowError: range() result has too many items
```

I know 12 digits is a huge number but... is there any way to get Python to do this operation regardless?

---

### Post by Soybean on 2007-07-25
Disclaimer: I know very little Python, but for some reason I seem to be trying to help with Python questions today. 

According to the python docs ([http://docs.python.org/lib/built-in-funcs.html#l2h-58](http://docs.python.org/lib/built-in-funcs.html#l2h-58)), the range function with a single parameter returns a list of all values from zero to that parameter. Now, I'm not sure what the maximum size for a list is in Python... but a list with 317584931803 elements is likely quite a bit larger than that maximum, if only because it's quite a bit larger than what could possibly fit in memory.

So I'm guessing that no, you probably can't convince it to do it anyway. ;) However, depending on what you were planning to do with that range, there may be another way to get the same effect. For example, perhaps you could loop through all the numbers from 0 to 317584931803 one at a time.

---

### Post by flummoxed on 2007-07-25
> **Soybean said:**
>  For example, perhaps you could loop through all the numbers from 0 to 317584931803 one at a time.

I like your thinking.

---

### Post by smartbei on 2007-07-25
Also (though this doesn't fix the actual problem) note that xrange has the same function but from my tests is faster for looping large numbers since it doens't create the whole list in the beginning - rather, it creates it as needed.

Besides, what do you mean by 'determining the range?

---

### Post by flummoxed on 2007-07-26
> **smartbei said:**
> 
Besides, what do you mean by 'determining the range?

As in... I have to go through every single one of the numbers in the range to check if they're prime or not.

I'm pretty sure doing a while loop that loops through all those numbers would crash python or take 3356 years to complete. I need to figure out some way to make the range function work with such a large number...

---

### Post by Wybiral on 2007-07-26
> **flummoxed said:**
> As in... I have to go through every single one of the numbers in the range to check if they're prime or not.

I'm pretty sure doing a while loop that loops through all those numbers would crash python or take 3356 years to complete. I need to figure out some way to make the range function work with such a large number...

With that that many iterations, it's going to take 3356 years in python either way you do it.

---

### Post by smartbei on 2007-07-26
Well, using python to find all the prime numbers under 317584931803 is probably not the greatest idea. This is not at all where python excels. Try using a C program like [http://pobox.com/~djb/primegen.html](http://pobox.com/~djb/primegen.html) to generate primes. If you must, have python read a file output by the program.

Though that too may be impractical - it takes my computer (see sig for info) 11 seconds to get the primes from 1 to 1000000000 and save them to a file (478mb!!!), and your range is more than 300 times that (note that the increase in time is **not** linear).

---

### Post by dwblas on 2007-07-26
I don't understand the advantage of storing all numbers in a list.  We discussed prime numbers before, and two things have been said (as far as I remember)
1. You only have to test up to the square root of the number +1
2. You can store the found primes in a list and test for those, ignoring all others in that range.  So if I am testing 9, I would divide by 2,3,5 and 7 and ignore the rest (4.6, &8 in this case).  Since half the numbers are even, dividing by the first prime in the list, 2, would eliminate half with only one pass.  Still, it's gonna take a long time.  HTH.

---

### Post by slavik on 2007-07-26
in C:
```

int isprime(long long int n) {
  long long int i = 3;
  long long int limit = (int)sqrt((float)n) + 1;
  if (n==2) return 1; /* 2 is prime */
  else if (n%2 == 0) return 0; /* even numbers are not prime */
  else {
    for (i =3; i<=limit; i+2) /* we know that this number is not even, therefore not divisible by 2, 4, 6, 8 */
      if (n % i == 0) return 0; /* not prime */
  }
  return 1; /* we didn't find a proper divisor */
}

```

---

### Post by Soybean on 2007-07-26
This site [http://krenzel.info/?p=83](http://krenzel.info/?p=83) has some information about finding primes, along with how long each method takes, and python implementations. Note that the fastest method here is the Sieve of Atkin, the same method used by the C program primegen, linked above. So primegen is presumably faster, but this might be good if you're trying to implement this as part of a larger python program or something.

---

### Post by pmasiar on 2007-07-27
> **smartbei said:**
>  note that xrange has the same function but from my tests is faster for looping large numbers since it doens't create the whole list in the beginning - rather, it creates it as needed.


xrange() returns iterator, so it return values as requested. Need be careful - don't try ie len(), it will have to generate all items in the list and you will lose benefit of it. 

You can create your own iterators with the yield statement.

---

### Post by pmasiar on 2007-07-27
> **flummoxed said:**
> I'm pretty sure doing a while loop that loops through all those numbers would crash python or take 3356 years to complete..

[numpy](http://en.wikipedia.org/wiki/Numpy) is faster way to do math calculations in Python.

BTW sorry for being late to this thread but poor choice of post title made me to ignore it. 

to OP: Next time give a hint at least which language you use :-)

---

