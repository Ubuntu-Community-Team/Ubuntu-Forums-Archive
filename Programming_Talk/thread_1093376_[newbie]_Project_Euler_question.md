---
title: "[newbie] Project Euler question"
date: 2009-03-11
forum: Programming Talk
---

### Post by tcoffeep on 2009-03-11
Hello.

I have recently written an answer to Project Euler in a few languages, ( Ruby, Perl, Python), and have a question. As to not give out the answer to anyone who wants to learn it for themselves, I request that someone who has knowledge of the three languages to PM me.
It is a matter of speed, and if there is any way I can make Ruby and Python work faster. I'm new to the languages, and have learned a few things thanks to PE, but there are still some quirks I need to sort out in regards to speed and functionality.

So, if anyone would be kind enough. I'd be extremely thankful.

Oh, and just to point out which question, specifically, it is Problem #25.

NOTE : I am not looking for answers, as I've stated. Merely looking to figure out how to be more precise with each style.

Ruby does it in : ~2.7 seconds
Python does it in : ~2.1 seconds
Perl does it in : 1 second

---

### Post by monkeyking on 2009-03-11
You should atleast give a link to the webpage.
Or even better make a copy paste.

Without more information, I can't help you.
But If you are using python32bit
Then look into the psycho package.
Good luck

---

### Post by tcoffeep on 2009-03-11
> The Fibonacci sequence is defined by the recurrence relation:

    F_(n) = F_(n&#8722;1) + F_(n&#8722;2), where F_(1) = 1 and F_(2) = 1.

Hence the first 12 terms will be:

    F_(1) = 1
    F_(2) = 1
    F_(3) = 2
    F_(4) = 3
    F_(5) = 5
    F_(6) = 8
    F_(7) = 13
    F_(8 ) = 21
    F_(9) = 34
    F_(10) = 55
    F_(11) = 89
    F_(12) = 144

The 12th term, F_(12), is the first term to contain three digits.

What is the first term in the Fibonacci sequence to contain 1000 digits?


From Project Euler.

Unfortunately, my Linux box is down until I get my power jack resoldered, so I'm doing this in vista. I think I read that in order to use psyco (sp?) in vista, I need cygwin, and I'm not sure how to implement it. It was rather buggy, last I used it.

---

### Post by monkeyking on 2009-03-11
ahh ok,
It really depends on your level of math,
but the fastest is most likely to use the binet formula [http://mathworld.wolfram.com/BinetsFibonacciNumberFormula.html](http://mathworld.wolfram.com/BinetsFibonacciNumberFormula.html) 
and then calculate modulo 1000

Other than that,
what have you done to make it faster.

You can meake it iterative quite easily instead of doing recursion.
Just go through an array and define the n`th element as the sum of the previous. Or something like  that.

---

### Post by tcoffeep on 2009-03-11
I'll have to look into that. Thanks.

---

### Post by vindvaki on 2009-03-11
I guess you could do it using Binet's formula, you may even be able to solve a general version of the problem by hand :)

However, it should be quite fast using a loop with two variables for the sequence, and one as a counter.

Runs in less than 0.1 seconds on my 2GHz Macbook 2,1 (OS X) in both ruby and python using that method.

---

### Post by tcoffeep on 2009-03-11
I do a loop between three variables, and one as a counter. It takes 2 seconds. Maybe it's because it's Vista? Or perhaps Python3k might run it faster? Or because I'm using the ActiveState release rather than the official Python installer?
And it takes Ruby 2.7 seconds, a whole 0.6 second difference, to do the same thing. Perhaps it's the usage of the extra variable?

And if that could be the case, why does Perl not have the same issue? (looping three variables + counter only takes it one second, or just under, as I could only count in seconds with it, not being able to find a more accurate timer.)

---

### Post by vindvaki on 2009-03-11
I haven't tried Perl, but in any case, 1-2 seconds sounds a bit much. In case you didn't know: You can compare your value to 10**999 (as that is the smallest 1000 digit number), as opposed to actually counting the digits.

Also, in order to be able to compare execution times you should always use the same method (otherwise, the result would be meaningless). For example, there is a cli program called time, which is probably included in Ubuntu and works for any executable. I use 
```
$ time python prob25.py 
``` 
I don't know if there is a Windows alternative. 

To see some alternative solutions, you can check the discussion about this problem at Project Euler (available only if you're logged in and have entered the correct answer).

Furthermore, if you're really interested in making your programs as fast as possible (by design), you can start by reading
[INDENT][http://en.wikipedia.org/wiki/Analysis_of_algorithms](http://en.wikipedia.org/wiki/Analysis_of_algorithms)[/INDENT]

---

### Post by monkeyking on 2009-03-11
Hi you asked for help in python, perl and ruby,
I don't know either, so I'll give a solution in c++.
Which shouldn't not help you too much :)

[PHP]
#include <iostream>
int main(){
  int fibs[1000]; //should be much more than enough
  fibs[0]=0;fibs[1]=1; //input start values
  int atPos = 2; //next pos in array to compute
  while(fibs[atPos-1]<1000){
    fibs[atPos] = fibs[atPos-1] +fibs[atPos-2];
    atPos++;
  }
  printf("fibs[%d]=%d\n",atPos,fibs[atPos-1]);
  return 0;
}
[/PHP]
I think the output was around fib ( 18 )=1597.
So in any programming language,
you should be able to implement it using 
16 comparisons, and 16 additions (without all the startup stuff).

If you need help understanding post back.

btw time used is 0.002 seconds

time ../a.out
fibs[18]=1597

real    0m0.002s
user    0m0.000s
sys     0m0.004s

---

### Post by tcoffeep on 2009-03-11
From the looks of it ( I've only done some basic C ) it goes up the fibonacci sequence until it reaches a number over 1000. What I'm looking for ( which is why I am using Perl, Python, and Ruby... because I already know how to switch between integers and strings. What the question is is finding a digit with 1000 characters.

I've never used arrays before, though. Would that, somehow, speed up the runtime?

---

### Post by eightmillion on 2009-03-11
I just did this problem with two variables and a counter as other have suggested, and it runs around .025 seconds:

[PHP]
#!/usr/bin/env python

a,b,x = 0,1,1
while b < ((10**999)-1):
    x += 1
    a,b = b,a+b
print x
[/PHP]

The pretty much identical ruby version takes a similar amount of time to run, although I had to move ((10**999)-1) out of the while loop because it appears that ruby calculates that value on every pass:
[PHP]
#!/usr/bin/env ruby

y = ((10**999)-1)
a,b,x = 0,1,1
while b < y
    x += 1
    a,b = b,a+b
end
puts x
[/PHP]

---

### Post by tcoffeep on 2009-03-11
> **eightmillion said:**
> I just did this problem with two variables and a counter as other have suggested, and it runs around .025 seconds:

[PHP]
#!/usr/bin/env python

a,b,x = 0,1,1
while b < ((10**999)-1):
    x += 1
    a,b = b,a+b
print x
[/PHP]

The pretty much identical ruby version takes a similar amount of time to run, although I had to move ((10**999)-1) out of the while loop because it appears that ruby calculates that value on every pass:
[PHP]
#!/usr/bin/env ruby

y = ((10**999)-1)
a,b,x = 0,1,1
while b < y
    x += 1
    a,b = b,a+b
end
puts x
[/PHP]


I tried that, and for some reason, it ran faster than the code I wrote. :(

Even my perl code.

---

### Post by eightmillion on 2009-03-11
> **tcoffeep said:**
> I tried that, and for some reason, it ran faster than the code I wrote. :(

Even my perl code.

What's your code look like? It shouldn't be too difficult to find out what's slowing it down.

---

### Post by tcoffeep on 2009-03-11
I wanted to avoid giving the answer, but since you've already done so, my python code :

```

a = 1
b = 0
c = 0
step = 1

while len(str(a)) < 1000:
    c = a + b
    b = a
    a = c
    step = step + 1
    if len(str(a)) == 1000:
        print(str(step))
```

My ruby :

```

a, b, c, step = 1, 1, 0, 2

while a.to_s.length < 1000
  c = a + b
  b = a
  a = c
  step = step + 1
end
puts step

```

My perl :

```

use bignum;
my $a = 1;
my $b = 0;
my $c = 0;
my $step = 1;
my $size = 0;
while($size<1000) {
  $c = $a + $b;
  $b = $a;
  $a = $c;
  $step++;
  $size = length($a);
  if($size == 1000) {
    print "$step\n";
  }
}

```

---

### Post by eightmillion on 2009-03-11
> **tcoffeep said:**
> I wanted to avoid giving the answer, but since you've already done so, my python code :



Why they're running slower is because on every pass of your loops, you're converting integers to strings to check the lengths. Type conversions are usually pretty slow. In your perl version, you don't have to do the conversion, but checking the length is probably still slower than just checking if the variable is greater than 10**999.

---

### Post by tcoffeep on 2009-03-11
Changing the perl code :

```

my $a = 0; my $b = 1; my $c = 0;
my $y = ((10**999)-1); my $x = 0;
while($a<$y) {
  $x++; $c = $a + $b; $b = $a; $a = $c;
}

print "$x\n";

```

It still takes a few ms longer than the ruby code ( or so it feels, as I can't find a command similar to linux's time command :( ).

---

### Post by eightmillion on 2009-03-11
> **tcoffeep said:**
> Changing the perl code :

```

my $a = 0; my $b = 1; my $c = 0;
my $y = ((10**999)-1); my $x = 0;
while($a<$y) {
  $x++; $c = $a + $b; $b = $a; $a = $c;
}

print "$x\n";

```

It still takes a few ms longer than the ruby code ( or so it feels, as I can't find a command similar to linux's time command :( ).

That takes just under a second on my box. I have almost no experience with perl, so I can't comment on why it takes so much longer. Maybe you could try using an array where you are adding the last two values in the array and checking that value and appending it to the array. In python, that would look like this:

[PHP]fibs = [0,1]

x = fibs[-1] + fibs[-2]
while x < (10**999)-1:
    fibs.append(x)
    x = fibs[-1] + fibs[-2]

print len(fibs)[/PHP]

Edit: It looks like that method is just as slow.
[PHP]use bignum;
@fibs = (0,1);
$y = ((10**999)-1);
$a = @fibs[-1] + @fibs[-2];
while($a<$y) {
  push(@fibs,$a);
  $a = @fibs[-1] + @fibs[-2];
}

print scalar(@fibs);[/PHP]

---

### Post by tcoffeep on 2009-03-11
Thanks to you, I've begun the descent into learning arrays. :)

Maybe I should focus in Python before I start using Perl and Ruby. My only problem with Python are little things, like the art of reversing the characters in a string ( ie : b = "Hello", b = b[::-1] making b = "olleH". I had to read a lot of stuff just to figure that out. Clean syntax, my ***! :P )

---

### Post by vindvaki on 2009-03-12
Hi, also an interesting and fast approach is using a generator in python:
[PHP]
def fibs():
    a, b = 0, 1
    while True:
        a, b = b, a+b
        yield a

n = 0
limit = 10**999
for f in fibs():
    n += 1
    if f >= limit:
        break
print(n) [/PHP]
In general, instead of actually thinking how you would do things by hand, try to imagine how your computer does things. For example, string operations tend to be expensive whereas simple numeric operations are usually fast.

Try to make sure your algorithm does only what is necessary to solve the problem. For example, to count the digits of a number you do not need to convert it to a string. To check an odd number for primality, it is enough to search for odd divisors up to the square root of the number.

A classic example is the [Sieve of Eratosthenes]("http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes")

In order to get a good feeling for these things, you can also read about classic algorithms such as quicksort vs. the much slower selection sort, and data structures such as arrays, linked lists and heaps etc. 

That, as well as my previous link to Algorithm Analysis at Wikipedia, should give you some idea of how you can design your programs to be fast, i.e. choosing how you store your data, avoiding repetition etc.

---

