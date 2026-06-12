---
title: "Prime generator perl"
date: 2010-11-28
forum: Programming Talk
---

### Post by Dorsenstein on 2010-11-28
I am using the following code for a prime generator in perl. 
```
#!/usr/bin/perl


use integer;

$max = 100;
@primes = (2 .. $max);
for ($i = 1, $i <= $max, $i++)
{
    $j = 2;
    while ($i * $j <= $primes[-1])
    {    
        if(exists $primes[$i*$j])
        {
            delete $primes[$i*$j];
        }
        $j++;
    }
}    
print @primes;
```However, it prints only odd numbers. 
If you could help fix it without modifying the method too much, it would be really appreciated.

---

### Post by cprofitt on 2010-11-28
If my meager math skills are correct... would not 2 be the only prime number that is even?

---

### Post by Dorsenstein on 2010-11-28
Ah, maybe I should have been more specific. It prints 3,5,7,9,11,13,15 etc. It doesn't filter out the odd numbers that aren't prime.

---

### Post by Arndt on 2010-11-28
> **Dorsenstein said:**
> Ah, maybe I should have been more specific. It prints 3,5,7,9,11,13,15 etc. It doesn't filter out the odd numbers that aren't prime.

So the first incorrect number is 9. It can't be that hard to go step by step in the algorithm and see what happens when it goes wrong. Try it.

---

### Post by Dorsenstein on 2010-11-28
> **Arndt said:**
> So the first incorrect number is 9. It can't be that hard to go step by step in the algorithm and see what happens when it goes wrong. Try it.

Sorry, i'm really not giving you the full problem. Here's the output i get.

```
234579111315171921232527293133353739414345474951535557596163656769717375777981838587899193959799
```I have no idea what's wrong. I converted it from this python code:
```
#!/usr/bin/env python
max = 1000000
primes = range(2, max+1)
for i in primes:
    j = 2
    while i*j <= primes[-1]:
        if i*j in primes:
            primes.remove(i*j)
        j += 1
print primes[-1]
```

---

### Post by cprofitt on 2010-11-28
got it... so you are really not seeing if a number is a prime or not.  Here is a Python test for a prime number. 
```

def is_prime(n):
    import math
    n = abs(n)
    i = 2
    while i <= n ** 0.5:
        if n % i == 0:
            return False
        i += 1
    return True

print is_prime(23)

```

---

### Post by Dorsenstein on 2010-11-28
I know. That's not what I'm trying to do. I'm trying to generate all the primes up to 100 using Eratosthenes sieve.

---

### Post by cprofitt on 2010-11-28
Here is Python code to do that:

```

def is_prime(n):
    import math
    n = abs(n)
    i = 2
    while i <= n ** 0.5:
        if n % i == 0:
            return False
        i += 1
    return True

max = 100
primes = range(2, max+1)

for i in primes:
    if is_prime(i):
        print(i)

```

---

### Post by Dorsenstein on 2010-11-28
> **cprofitt said:**
> Here is Python code to do that:

```

def is_prime(n):
    import math
    n = abs(n)
    i = 2
    while i <= n ** 0.5:
        if n % i == 0:
            return False
        i += 1
    return True

max = 100
primes = range(2, max+1)

for i in primes:
    if is_prime(i):
        print(i)

```

Nah, but that's not what I'm trying to do. I'm using Eratosthenes sieve to do it. And I already did it in Python, tried to port it to Perl, and it didn't work. So I'm trying to figure out why.

---

### Post by conradin on 2010-11-28
I don't feel like writing any more code today, but here's a thought:
if the Eratosthenes sieve is used on 10 rather than 100, the first run could put the 2-10 in an array. Then check 2-10 indexes for prime numbers.
Then put 11-20 in the array and increment the index. The next pass would be 3-10, until you read the end of the your data set. I'm pretty sure that's how the Eratosthenes sieve works anyway.

---

### Post by nvteighen on 2010-11-28
Uhm...

Is "if i*j in primes: ..." the same as "if(exists primes[i*j]) { ... }"?

Also, there are much easier ways to write the Sieve.

---

### Post by Arndt on 2010-11-28
You may want to look at the syntax of 'for' loops in Perl. And do what I suggested: go through the code step by step and print things out meanwhile. You will see where Perl doesn't behave like Python.

---

### Post by shawnhcorey on 2010-11-28
Always put these lines at the start of you script:
```
use strict;
use warnings;
```

You have to load 0 and 1 into the start of the array so that the index and the value are the same.

```
#!/usr/bin/perl

use strict;
use warnings;

use integer;

my $max = 100;
my @primes = (0 .. $max);
for my $i ( 2 .. sqrt( $max ) ){
    for my $j ( $i .. $primes[-1] ){
        delete $primes[$i*$j];
    }
}    

@primes = grep { $_ } @primes;
print "@primes\n";


```

---

### Post by Dorsenstein on 2010-11-28
> **shawnhcorey said:**
> 

```
#!/usr/bin/perl

use strict;
use warnings;

use integer;

my $max = 100;
my @primes = (0 .. $max);
for my $i ( 2 .. sqrt( $max ) ){
    for my $j ( $i .. $primes[-1] ){
        delete $primes[$i*$j];
    }
}    

@primes = grep { $_ } @primes;
print "@primes\n";


```

Ah thank you so much. I didn't know that you could use ranges in for loops like python.

---

### Post by shawnhcorey on 2010-11-28
> **Dorsenstein said:**
> Ah thank you so much. I didn't know that you could use ranges in for loops like python.

You can use a range any where you can use a list.  A range will generate each item as needed.  But sometimes it will create a list:

```
sub foo {
  for my $i ( @_ ){
    print "$i\n";
  }
}

foo( 1 .. 1_000_000 );  # sends the whole list to foo()
```

---

