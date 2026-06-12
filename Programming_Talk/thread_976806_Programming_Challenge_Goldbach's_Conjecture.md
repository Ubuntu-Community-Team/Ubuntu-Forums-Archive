---
title: "Programming Challenge: Goldbach's Conjecture"
date: 2008-11-09
forum: Programming Talk
---

### Post by tom66 on 2008-11-09
**Goal: ** Write a program which calculates [Goldbach's conjecture](http://en.wikipedia.org/wiki/Goldbach%27s_conjecture); that is, it shows the two primes needed to reach a specific number.

**Bonuses: ** 
[list]
[*] Show the [Weak conjecture](http://en.wikipedia.org/wiki/Goldbach%27s_weak_conjecture), as well.
[*] Show all the possibles, and count them.
[*] Optionally support using more than two numbers to get there, like the weak conjecture, but see if it can be done with 2, 3, 4, 5, 6, etc. numbers, as well.
[*] Make your programs as fast as possible.
[/list]

---

### Post by tom66 on 2008-11-09
Well, here's my entry, in C.

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

#define MAX_NUM 500000

int _max = 100;
int* _primes;

int is_prime(int calc)
{
	if(calc == 2) return 1;
	else
	{
		if(calc % 2 == 0) return 0;
		else
		{
			int i = 3;
			int max = (int)sqrt(calc);
		
			for(; i <= max; i += 2) /* Faster than i++, but produces identical results (2 is the only even prime) */
			{
				if(calc % i == 0) return 0;
			}
		
			return 1;
		}
	}
}

int main(int argc, char *argv[])
{
	int i = 3, k = 1, j = 1; /* Start k/j = 1 because we're setting first prime. */
	double perc, last_perc;
	_primes = malloc(sizeof(int) * MAX_NUM);
	_primes[0] = 2; /* 2 is prime; only even prime. */
	
	printf("Calculating primes up to %d... \n", MAX_NUM);
	
	/* Calculate all primes. */
	for(; i <= MAX_NUM; i += 2)
	{
		if(is_prime(i) == 1)
		{
			_primes[k] = i;
			k++;
			j++;
		}
		
		if(i % 101 == 0) /* Note odd number here; we go up in odd numbers, so even would never show up. */
		{
			perc = (((double)i / (double)MAX_NUM) + 0.0) * 100; /* Ensure number is double. */
			
			if(floor(perc) != floor(last_perc))
			{
				printf("%1.1f%% done... (found: %d primes)\n", perc, j);
				last_perc = perc;
				j = 0;
			}
		}
	}
	
	printf("Done. Adjusting array... \n");
	
	/* Adjust the array. */
	_primes = (int *)realloc(_primes, sizeof(int) * k);
	printf("Done. Calculating Goldbach's Conjecture... \n");
	
	/* Go through each even number and try to find two primes which divide into it. */
	int p = 0, q = 0;
	int pv = 0, qv = 0;
	int solutions = 0;
	char sol[100];
	
	for(i = 4; i < MAX_NUM; i += 2)
	{
		solutions = 0;
		
		for(p = 0; p < i; p++)
		{
			pv = _primes[p];
			
			for(q = 0; q < i; q++)
			{
				qv = _primes[q];
				
				if((pv + qv) == i)
				{
					solutions++;
					
					if(solutions == 1)
					{
						sprintf(sol, "%d + %d", pv, qv);
						p = i;
						q = i;
					}
				}
			}
		}
		
		if(solutions > 0)
		{
			printf("Solved for %d (sample: %s). \n", i, sol);
		}
		else
		{
			printf("Not solved for %d\n", i);
			exit(0);
		}
	}
}

```

---

### Post by tiachopvutru on 2008-11-09
My entry in Python 2.5.

[PHP]import math

#this function checks whether a number is a prime
def isprime(num):
    if num < 2: return False
    elif num == 2: return True
    elif num % 2 == 0: return False
    else:
        check = 3
        while check <= math.sqrt(num):
            if num % check == 0:
                return False
            check += 2
    return True

#this function finds Golbach Conjecture
#if Golbach's Conjecture isn't true, this function will go into an infinite loop
def findGolCon(num):
    answer1 = num / 2
    if isprime(answer1):
        return answer1, answer1
    else:
        answer2 = answer1
        while not isprime(answer1) or not isprime(answer2):
            answer1 -= 1
            answer2 += 1
        return answer1, answer2

if __name__ == "__main__":
    for x in xrange(4, 101, 2):
        print findGolCon(x)[/PHP]

Didn't do the bonuses, though...

---

### Post by Luggy on 2008-11-09
Here is a very basic approach for python that only finds Goldbach values with two primes:
[PHP]
# this is how high to go up to
limit = 50

# return True or False if a value is prime or not
def isPrime( value ):
	prime = True
	for i in range(2,value):
		if( value % i == 0 ):
			prime = False
			break
	return prime

# Build a list of all primes up to the limit value		
primeList = []
for i in range(2,limit):
	if( isPrime(i) ):
		primeList.append(i)

# Finds two values from primeList that sum value
# Some checking is also put in place to avoid repeated values. ie: 3 + 7
# and 7 + 3
def goldBach(value):
	usedList = []
	for i in primeList:
		for j in primeList:
			if( i + j == value ):
				wasUsed = False
				for x in usedList:
					if( i == x or j == x ):
						wasUsed = True
				if( not wasUsed ):
					print str(value) + ' = ' + str(i) + ' + ' + str(j)
					usedList.append(i)
					usedList.append(j)

# Find all goldBach values from 2 to the limit value
for i in range(2, limit):
	goldBach(i)
[/PHP]

---

### Post by CptPicard on 2008-11-09
EDIT: Ok, version 2 ;)

Something rather simple in Scheme:

```

(define (range start end)
  (if (> start end)
      '()
      (cons start
            (range (+ start 1) end))))


(define (filter pred li)
  (if (null? li)
      '()
      (if (pred (car li))
          (cons (car li)
                (filter pred (cdr li)))
          (filter pred (cdr li)))))


(define (primes max)
  (let loop ((sieve-list (range 2 max)))
    (if (> (car sieve-list) (sqrt max))
        sieve-list
        (cons (car sieve-list)
              (loop
               (filter 
                (lambda (x) 
                  (not
                   (= (remainder x (car sieve-list)) 0)))
                (cdr sieve-list)))))))


(define (goldbach-pairs num)

  (define (all-pairs li)
    (let top-loop ((top-list li) (acc '()))
      (if (null? top-list)
          acc
          (let sub-loop ((sub-list top-list) (sub-acc acc))
            (cond ((or (null? sub-list) (> (+ (car top-list) (car sub-list)) num))
                   (top-loop (cdr top-list) sub-acc))
                  ((= (+ (car top-list) (car sub-list)) num)
                   (sub-loop (cdr sub-list) (cons (cons (car top-list) (car sub-list)) sub-acc)))
                  (else
                   (sub-loop (cdr sub-list) sub-acc)))))))
  
  (if (not (= (remainder num 2) 0))
      '()
      (all-pairs (primes num))))

; Then in REPL...

> (goldbach-pairs 1024)
((503 . 521) (467 . 557) (461 . 563) (431 . 593) (383 . 641) (347 . 677) (281 . 743) (263 . 761) (251 . 773) (227 . 797) (197 . 827) (167 . 857) (137 . 887) (113 . 911) (83 . 941) (71 . 953) (53 . 971) (47 . 977) (41 . 983) (11 . 1013) (5 . 1019) (3 . 1021))

> (goldbach-pairs 10206)
((5099 . 5107) (5087 . 5119) (5059 . 5147) (5039 . 5167) (5009 . 5197) (4973 . 5233) (4969 . 5237) (4933 . 5273) (4909 . 5297) (4903 . 5303) (4813 . 5393) (4799 . 5407) (4793 . 5413) (4789 . 5417) (4787 . 5419) (4729 . 5477) (4723 . 5483) (4703 . 5503) (4679 . 5527) (4649 . 5557) (4643 . 5563) (4637 . 5569) (4583 . 5623) (4567 . 5639) (4549 . 5657) (4547 . 5659) (4523 . 5683) (4517 . 5689) (4513 . 5693) (4463 . 5743) (4457 . 5749) (4423 . 5783) (4363 . 5843) (4357 . 5849) (4349 . 5857) (4339 . 5867) (4337 . 5869) (4327 . 5879) (4283 . 5923) (4253 . 5953) (4219 . 5987) (4177 . 6029) (4159 . 6047) (4153 . 6053) (4139 . 6067) (4133 . 6073) (4127 . 6079) (4093 . 6113) (4073 . 6133) (4007 . 6199) (4003 . 6203) (3989 . 6217) (3943 . 6263) (3929 . 6277) (3919 . 6287) (3907 . 6299) (3889 . 6317) (3877 . 6329) (3863 . 6343) (3853 . 6353) (3847 . 6359) (3833 . 6373) (3779 . 6427) (3733 . 6473) (3677 . 6529) (3659 . 6547) (3643 . 6563) (3637 . 6569) (3607 . 6599) (3547 . 6659) (3533 . 6673) (3527 . 6679) (3517 . 6689) (3469 . 6737) (3413 . 6793) (3373 . 6833) (3343 . 6863) (3323 . 6883) (3307 . 6899) (3299 . 6907) (3259 . 6947) (3257 . 6949) (3229 . 6977) (3209 . 6997) (3187 . 7019) (3167 . 7039) (3163 . 7043) (3137 . 7069) (3079 . 7127) (3019 . 7187) (2999 . 7207) (2969 . 7237) (2963 . 7243) (2953 . 7253) (2909 . 7297) (2897 . 7309) (2857 . 7349) (2837 . 7369) (2789 . 7417) (2749 . 7457) (2729 . 7477) (2719 . 7487) (2707 . 7499) (2699 . 7507) (2689 . 7517) (2683 . 7523) (2677 . 7529) (2659 . 7547) (2657 . 7549) (2647 . 7559) (2633 . 7573) (2617 . 7589) (2557 . 7649) (2503 . 7703) (2447 . 7759) (2417 . 7789) (2389 . 7817) (2383 . 7823) (2377 . 7829) (2339 . 7867) (2333 . 7873) (2287 . 7919) (2273 . 7933) (2269 . 7937) (2243 . 7963) (2213 . 7993) (2153 . 8053) (2137 . 8069) (2113 . 8093) (2089 . 8117) (2083 . 8123) (2039 . 8167) (2027 . 8179) (1997 . 8209) (1987 . 8219) (1973 . 8233) (1933 . 8273) (1913 . 8293) (1889 . 8317) (1877 . 8329) (1787 . 8419) (1783 . 8423) (1777 . 8429) (1759 . 8447) (1693 . 8513) (1669 . 8537) (1667 . 8539) (1663 . 8543) (1609 . 8597) (1607 . 8599) (1597 . 8609) (1583 . 8623) (1579 . 8627) (1559 . 8647) (1543 . 8663) (1499 . 8707) (1493 . 8713) (1487 . 8719) (1459 . 8747) (1453 . 8753) (1427 . 8779) (1423 . 8783) (1399 . 8807) (1367 . 8839) (1319 . 8887) (1283 . 8923) (1277 . 8929) (1237 . 8969) (1193 . 9013) (1163 . 9043) (1103 . 9103) (1097 . 9109) (1069 . 9137) (1049 . 9157) (1033 . 9173) (1019 . 9187) (997 . 9209) (967 . 9239) (929 . 9277) (887 . 9319) (883 . 9323) (863 . 9343) (857 . 9349) (829 . 9377) (809 . 9397) (787 . 9419) (773 . 9433) (769 . 9437) (743 . 9463) (739 . 9467) (733 . 9473) (727 . 9479) (709 . 9497) (673 . 9533) (659 . 9547) (619 . 9587) (593 . 9613) (587 . 9619) (577 . 9629) (563 . 9643) (557 . 9649) (509 . 9697) (487 . 9719) (467 . 9739) (463 . 9743) (457 . 9749) (439 . 9767) (419 . 9787) (389 . 9817) (373 . 9833) (367 . 9839) (349 . 9857) (347 . 9859) (283 . 9923) (277 . 9929) (257 . 9949) (239 . 9967) (233 . 9973) (199 . 10007) (197 . 10009) (167 . 10039) (139 . 10067) (137 . 10069) (127 . 10079) (113 . 10093) (107 . 10099) (103 . 10103) (73 . 10133) (67 . 10139) (47 . 10159) (43 . 10163) (37 . 10169) (29 . 10177) (13 . 10193))


```

All pure-functional too. :) Note how the "all-pairs" function is essentially two nested loops (tail-recursive functions expressed as named lets). It even flirts with the concept of continuation, which in pure-functional programming actually is much clearer a concept because we're dealing with substitution of expressions anyway, so "handing computation over" to the continuation function doesn't look nearly as strange (actually there is no difference whatsoever to business as usual in pure-functionality) as it does in languages with mutable state...

---

### Post by samjh on 2008-11-10
Here's a naive attempt, using Ada. [EDIT: Version 2. Now checks that the number is even.]

To compile, the GNAT compiler is required ([FONT="Courier New"]sudo apt-get install gnat[/FONT]):
1. Save as [FONT="Courier New"]goldbach.adb[/FONT]
2. [FONT="Courier New"]gnat make goldbach.adb[/FONT]

Example usage:
[FONT="Courier New"]./goldbach 100
Result: 100 = 3 + 97[/FONT]
```
with Ada.Text_IO;
with Ada.Integer_Text_IO;
with Ada.Command_Line;
use Ada.Text_IO;
use Ada.Integer_Text_IO;
use Ada.Command_Line;

procedure Goldbach is
	Target, A1, A2 : Integer;

	function IsPrime (N: Integer) return Boolean is
		Result : Boolean := True;
	begin
		for C in Integer range 2..(N-1) loop
			if N mod C = 0 then
				Result := False;
				exit;
			end if;
		end loop;
		return Result;
	end IsPrime;

	procedure FindGold (A1, A2: in out Integer) is
	begin
		if IsPrime(A1) = False or IsPrime(A2) = False then
			A1 := A1 + 1;
			A2 := Target - A1;
			FindGold(A1, A2);
		end if;
	end FindGold;

begin
	Target := Integer'Value(Argument(1));
	if Target < 4 then
		Put_Line("Sorry, too small. Value must be at least 4.");
	else if Target mod 2 /= 0 then
		Put_Line("Sorry, the value must be even.");
		else
			A1 := 2;
			A2 := Target - A1;
			FindGold(A1, A2);
			Put_Line(Argument(1) & " =" & A1'Img & " +" & A2'Img);
		end if;
	end if;
end Goldbach;
```


And *almost* identical translation into C++, just for kicks. :p:
```
#include <iostream>
#include <cstdlib>

using namespace std;

bool is_prime(int n)
{
	bool result = 1;
	int c;
	for (c = 2; c < n; c++)
	{
		if (n % c == 0)
		{
			result = 0;
			break;
		}
	}
	return result;
}

void find_gold(int max, int& a1, int& a2)
{
	if ((is_prime(a1) && is_prime(a2)) == false)
	{
		a1 = a1 + 1;
		a2 = max - a1;
		find_gold(max, a1, a2);
	}
}

int main(int argc, char* argv[])
{
	int target, a1, a2;
	target = atoi(argv[1]);
	if (target < 4)
	{
		cout << "Sorry, too small. Value must be at least 4." << endl;
	}
	else
	{
		if (target % 2 != 0)
		{
			cout << "Sorry, the value must be even." << endl;
		}
		else
		{
			a1 = 2;
			a2 = target - a1;
			find_gold(target, a1, a2);
			cout << target << " = " << a1 << " + " << a2 << endl;
		}
	}
	return 0;
}
```

The C++ implementation is around 20% faster for calculating 2,000,000; but only 2% faster for calculating 20,000,000.  Strange.

---

### Post by nvteighen on 2008-11-11
Here it is. I did this as a Perl learning exercise... quite simple, too (but the Scheme one rocks), but I got it finished rather slow because I'm not aware what's on the language and what's not.

```

#!/usr/bin/env perl

# UF Programming Challenge: Goldbach's Conjecture (Perl 5.10)

use strict;

sub primes{
    # Generates the array of primes up to given number.
    #
    # ARG: 
    # $max: A scalar integer value.
    #
    # RET: The array of primes up to $max. If there are no primes or the
    # argument is invalid, it returns ().

    my $max = shift;
    return () if (($max < 2) or ($max ne int($max)));
    
    my @primes = ();
    my @list = (2..$max);

    # Using the Sieve of Eratosthenes.
    until(@list == 0){
        @primes[++$#primes] = @list[0];
        @list = grep {$_ % @primes[$#primes] != 0} @list;
    }
        

    return @primes;
}

sub goldbach{
    # Solves the Goldbach problem for a given number.
    #
    # ARG:
    # $number: A scalar integer value.
    #
    # RET: Returns an array of array references to the pairs of primes.

    my $number = shift;

    my @primes = primes $number;
    
    my @ret = ();
    foreach my $first (@primes){
        foreach my $second (reverse @primes){
            last if ($first > $second); # Breaking when we start duplicating.
            
            # We use array references to avoid interpolation.
            @ret[++$#ret] = [$first, $second] if ($first + $second == $number);
        }
    }
    
    return @ret;
}

sub main{
    # Main procedure... A C-ish custom, I guess.

    print "Goldbach Programming Challenge\nEnter a number:";

    chomp (my $number = <STDIN>);
    die "$number not a real number!" if ($number ne int($number));

    my @goldbach = goldbach $number;

    foreach my $pair (@goldbach){
        print "(@$pair[0] . @$pair[1]) "; # Output à la Lisp.
    }
}

main;

```

---

### Post by phillipi on 2009-11-25
C++, just outputs two primes that equal a given even number

```
#include <iostream>
#include <math.h>
using namespace std;

int main() {
	int testnumber;		// this is the number to be tested
	int prime1;
	int prime2;
	int is_prime1;
	int is_prime2;
	int counter;
	int i;
	int solution1;
	int solution2;
	
	cout << "The purpose of this program is to prove Goldbach's conjecture" << endl;
	cout << "Please input a number to be tested and press ENTER: ";
	cin >> testnumber;

	prime1 = 1;
	prime2 = 1;	

	for (counter = 1; counter <= testnumber; counter++) {
		prime1 = prime1 + 1;		
	
		is_prime1 = true;							// this block tests to see if prime1 is prime
		for (i = 2; i <= sqrt((double)prime1); i++) {
			if (prime1 % i == 0)
				is_prime1 = false;
		}

		if (is_prime1 == true) {						// this block is only run if prime1 is prime
			prime2 = testnumber - prime1;

			is_prime2 = true;						// this block tests to see if prime2 is prime
			for (i = 2; i <= sqrt((double)prime2); i++) {
				if (prime2 % i == 0)
				is_prime2 = false;
			}
		}

		if (is_prime1) {							// if prime1 is prime
			if (is_prime2) {						// and if prime2 is prime
				if (prime1 + prime2 == testnumber)			// and finally if prime1 + prime2 = the testnumber
					if (prime2 >= 2) {
						solution1 = prime1;		// save the solution for output
						solution2 = prime2;
					}
			}
		}
	}
	cout << "Goldbach's conjecture is proven again: " << solution1 << " + " << solution2 << " = " << testnumber << endl;

return 0;

}

```

---

### Post by cirodurso on 2012-09-10
> **tom66 said:**
> **Goal: **Write a program which calculates [Goldbach's conjecture]("http://en.wikipedia.org/wiki/Goldbach%27s_conjecture"); that is, it shows the two primes needed to reach a specific number.
 
 

**Bonuses: **
[LIST]
[*]Show the [Weak conjecture]("http://en.wikipedia.org/wiki/Goldbach%27s_weak_conjecture"), as well.
[*]Show all the possibles, and count them.
[*]Optionally support using more than two numbers to get there, like the weak conjecture, but see if it can be done with 2, 3, 4, 5, 6, etc. numbers, as well.
[*]Make your programs as fast as possible.
[/LIST]
 
Is there anyone that could use the following approach in order to find the Goldbach pairs?
 
[http://arxiv.org/abs/1208.2244](http://arxiv.org/abs/1208.2244)
 
Let me know
Thanks

---

### Post by Lux Perpetua on 2012-09-10
It should be easy, since your method is elementary. However, I'm stuck on part of your argument: near the top of page 9, you make the assertion that P_i*P_i' <= pi(sqrt(2*e))*sqrt(2*e). I agree that P_i' < p_i <= sqrt(2*e), but I don't think the inequality follows. For example, with e = 25, sqrt(2*e) = 7.07106... and pi(sqrt(2*e)) = 4. For p_i = 7, we have P_i = 2*3*5 = 30 and P_i' = 4, so P_i*P_i' = 120, which is much greater than pi(sqrt(2*e))*sqrt(2*e) = 4*7.07106 = 28.284271.... 

Did I misinterpret something?

---

