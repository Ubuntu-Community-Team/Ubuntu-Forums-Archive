---
title: "isPrime? Are you prime? I need help lol."
date: 2008-07-20
forum: Programming Talk
---

### Post by ogwilson on 2008-07-20
Obviously I'm not the greatest mathematician or problem solver in the world, so bear with me. I'm making a program that loops through numbers one by one, checking to see if they're prime, and if so, it'll print out the number. 10 numbers per line. Here's my source.

[http://pastebin.com/mf31414b](http://pastebin.com/mf31414b)

the source is a modified version of a problem in my book. I'm simply supposed to rewrite the program that uses an isPrime method rather than doing everything in main. Knowing this, i coded everything that isPrime is supposed to do, and just copied/pasted everything else around it. i thought it'd have the same effect, but to no avail. Can anyone PLEASE help me out. It'd be greatly appreciated.

---

### Post by Tony Flury on 2008-07-20
What is the output when you run this - i am no java expert, but if you show the output we might be able to help.

---

### Post by ogwilson on 2008-07-20
The output is literally blank.

---

### Post by Tony Flury on 2008-07-20
How odd.

A few more questions  : 

Does the program exit ? or is it hanging ?

Do you have a debuger that alllows you to step through the code ?

as i say - I am not a java expert (so it might be some syntax nuance) but at first glance the logic looks right - apart from one thing -

should your while loop line 12 - not be 

```

while (number < PRIMES)

```

the way you have it - it will try to print the first 999 primes, instead of all primes from 1 to 999.

---

### Post by gekkio on 2008-07-20
```
for(int divisor = 2; divisor <= number / 2; divisor++)
```

When the program executes this line,
divisor = 2
number = 2, so number / 2 = 1
So, the condition in the for loop (divisor <= number / 2) is never true, because 2 <= 1 is not true and the for loop is never executed.
And because number is never modified except in the for loop, the while loops happily until count == PRIMES and nothing is ever printed.
This is the problem unless I missed something.

---

### Post by Tony Flury on 2008-07-20
Well spotted gekko, and also since count is incremented inside the loop too, the program will just spin,

The increment of number (line 30)  needs to be outside the for loop - but inside the while loop.

I would suggest swapping lines 30 and 31.

---

### Post by Replicon on 2008-07-20
This might interest you:

[http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes](http://en.wikipedia.org/wiki/Sieve_of_Eratosthenes)


Also, you only need to check previous primes up to the sqrt of the number (not half).

---

### Post by Can+~ on 2008-07-20
Also, you should increment each 2, there are no primes divisible by 2 except for.. 2.

---

### Post by ogwilson on 2008-07-20
after swapping lines 30 and 31, here's the new output

[http://pastebin.com/m73f8fc39](http://pastebin.com/m73f8fc39)

im sorry if i seem like im just trying to get quick answers. I really can't see what i would be doing wrong. I figured the for loop w/ divisor was the problem, but I don't know why this would be? My book's algorithm says it should be from 2 up to number divided by 2.

---

### Post by StOoZ on 2008-07-20
this is how I did that :
> #include<iostream>
using namespace std;

void list_primes(int f,int l);
bool check_prime(int num);



int main()
{
int lower,higher;
cout<<"Please enter the lower range :";
cin>>lower;
cout<<"Please enter the higher range :";
cin>>higher;
list_primes(lower,higher);

 return 0;
}


//a function which takes two arguments and checks the numbers between them
// (including them), and list all the prime numbers.
//this function calls the 'check_prime' function.
void list_primes(int f,int l)
{
  int *d_ptr_primes_table = new int[l-f];
  int counter=0;
  for (int i=f;i<=l;i++)
  {
      if (check_prime(i))
      {
          d_ptr_primes_table[counter] = i;
          counter++;
      }
  }
  cout<<"Listing Prime numbers in ["<<f<<" - "<<l<<"] range:\n";
  for (int z=0;z<counter;z++)
  {
      if (z%10==0)
          cout<<"\n";

      cout<<d_ptr_primes_table[z]<<" | ";
  }
  delete []d_ptr_primes_table;
}


// a function which cheks whether a number is a prime or not :
// prime --> true (1)
// not prime --> false(0);
bool check_prime(int num)
{
    bool flag=true;
    for (int i=2;i<num;i++)
    {
        if (num%2==0 || num%i==0)
            flag=false;
    }
    return flag;
}




---

### Post by Lster on 2008-07-20
[QUOTE=Can+~]Also, you should increment each 2, there are no primes divisible by 2 except for.. 2.[/QUOTE]

In addition to this, you can gain a coefficient speed increase by using the fact that, except for 2 and 3, all primes can be written in the form 6k±1.

Using that fact gives this code:

[PHP]
public class Main {
    
    public static boolean isPrime(int x)
    {
        if(x <= 1) return false;
        if(x <= 3) return true;
        if(x%2 == 0) return false;
        if(x%3 == 0) return false;
        
        int s = (int)Math.sqrt(x);
        int i = 5;
        while(i <= s)
        {
            if(x%i == 0) return false;
            i += 2;
            if(x%i == 0) return false;
            i += 4;
        }
        return true;
    }

    public static void main(String[] args) {
        for(int i = 1; i < 100; i++)
        {
            if(isPrime(i)) System.out.println(i);
        }
    }

}
[/PHP]

It's worth checking the code for any bugs as it isn't thoroughly checked!

---

### Post by ogwilson on 2008-07-20
Thanks for the help guys. I'm going to take my code and compare it with you guys' and lets see what I can do =). This is by far the most helpful programming forum i've ever been on.

---

### Post by Reiger on 2008-07-20
Heh, gotta love Haskell for this kind of stuff, eh?

```

module Test where

sift x lst = filter  ((/=0) .(`mod` x) ) lst
siftAll (x:[]) = [x]
siftAll (x:xs) = x : siftAll (sift x xs)
primes low up 
	| up == (-1) = siftAll [low..]
	| otherwise = siftAll [low..up]

```

Using 2 & -1 --> all primes in existance. Using arbitrary values k>=2 & m>=k in the expression "primes k m" results in all values *relatively prime* to all other values *inside* the specified interval. Using k & -1 evaluates to all primes in existance >= k plus all other values relatively prime to all other values within the interval.

---

### Post by Can+~ on 2008-07-20
> **Lster said:**
> In addition to this, you can gain a coefficient speed increase by using the fact that, except for 2 and 3, all primes can be written in the form 6k±1.

Using that fact gives this code:

It's worth checking the code for any bugs as it isn't thoroughly checked!

I never noticed that, I had to do it:
[PHP]#!/usr/bin/env python

import time

def timer(func):
	def wrapper(*args, **kargs):
		time_a = time.time()
		ret = func(*args, **kargs)
		time_b = time.time()
		
		print "\nExecution Time: %f [s]" % (time_b-time_a)
		
		return ret
	return wrapper

def prime_generator(limit):
	"""5 and 7 are primes, both are 6-1, 6+1. 11 and 13.. etc."""
	
	tester = lambda x: x%5 and x%7
	
	#Initial condition.
	for lowestprime in (1, 2, 3, 5, 7):
		yield lowestprime
	
	#Multiples of 6
	for multsix in xrange(6, limit, 6):
		if tester(multsix-1): yield multsix-1
		if tester(multsix+1): yield multsix+1

@timer
def request(limit):
	for i in prime_generator(limit):
		print i,

request(1000)[/PHP]

Added a timer decorator to measure time.

Output:
```
1 2 3 5 7 11 13 17 19 23 29 31 37 41 43 47 53 59 61 67 71 73 79 83 89 97 101 103 107 109 113 121 127 131 137 139 143 149 151 157 163 167 169 173 179 181 187 191 193 197 199 209 211 221 223 227 229 233 239 241 247 251 253 257 263 269 271 277 281 283 289 293 299 307 311 313 317 319 323 331 337 341 347 349 353 359 361 367 373 377 379 383 389 391 397 401 403 407 409 419 421 431 433 437 439 443 449 451 457 461 463 467 473 479 481 487 491 493 499 503 509 517 521 523 527 529 533 541 547 551 557 559 563 569 571 577 583 587 589 593 599 601 607 611 613 617 619 629 631 641 643 647 649 653 659 661 667 671 673 677 683 689 691 697 701 703 709 713 719 727 731 733 737 739 743 751 757 761 767 769 773 779 781 787 793 797 799 803 809 811 817 821 823 827 829 839 841 851 853 857 859 863 869 871 877 881 883 887 893 899 901 907 911 913 919 923 929 937 941 943 947 949 953 961 967 971 977 979 983 989 991 997 
Execution Time: 0.000435 [s]
```

---

### Post by Lster on 2008-07-21
It's quite easy to prove too:

If you consider all integers, n, can be expressed as exactly one of these:

[INDENT]6k
6k+1
6k+2
6k+2
6k+3
6k+4
6k+5[/INDENT]

All integers expressible as 6k are divisible by 2 and 3 and are thus not prime. All of the form 6k+2 are even... All of the form 6k+3 are divisible by 3... All of the 6k+4 are even...

Thus, we are left with:

[INDENT]6k+1
6k+5[/INDENT]

Or 6k±1. I *imagine* (haven't tried it!) the same can be done with other integers, a, in the form: ak+[o[0], o[1], o[2], ...]. Where o[x] is a possible offset.

---

