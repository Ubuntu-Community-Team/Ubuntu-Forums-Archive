---
title: "Am i Wrong??"
date: 2012-09-25
forum: Programming Talk
---

### Post by Mohan1289 on 2012-09-25
Hey Guys i am trying to solve a Problem

For that i thought an Algorithm Tell me if i am wrong..

If i am wrong tell me where and why?

The Question is 

[COLOR="Red"]A palindromic number reads the same both ways. The largest palindrome made from the product of two 2-digit numbers is 9009 = 91 99.

Find the largest palindrome made from the product of two 3-digit numbers.[/COLOR]

The Algorithm I thought is:
[COLOR="Blue"]

1.Create a for loop which repeats from 100-999 like

     for(i=100;i<999;i++)

2. In the above for-loop create another for-loop which repeats from 100-999 again
     for(j=100;j<999;j++)
3. Then multiply i with j;

4. Store the result in a Variable.

5. Check weather the value is Palindrome or not by reversing the value and comparing with the result
6. If true store the value in another variable
7. Else repeat the Loop again
8. Close all the For-Loops 
9. And finally Print the Palindrome number.
[/COLOR]

Then again the algorithm seems correct to me but i got a doubt.

Do i have to compare the result with the stored palindrome number??

Does that repeat it self until it's largest palindrome number???

I know it's Brute Forcing but i couldn't think of another solution.

Any Idea's??
Am i Mistaken??

---

### Post by Bachstelze on 2012-09-25
You also need to store the largest palindrome that you have found so far. When you find a new palindrome, compare it with the stored one. If it's larger, it's the new "largest palindrome".

---

### Post by Mohan1289 on 2012-09-25
> **Bachstelze said:**
> You also need to store the largest palindrome that you have found so far. When you find a new palindrome, compare it with the stored one. If it's larger, it's the new "largest palindrome".

hmmm Why???

The for-loop will automatically repeats until the result is largest doesn't it??

Then why save the Largest Palindrome number in a separate Variable

---

### Post by Bachstelze on 2012-09-25
> **Mohan1289 said:**
> 
The for-loop will automatically repeats until the result is largest doesn't it??

No.

---

### Post by Mohan1289 on 2012-09-25
Why?
The for-loop is for repeating itself until the conditions are satisfied right?

Like if you are trying to get Prime Numbers we have to use two For-loops

for(i=0;i<range;i++
{
  for(j=0;j<i;j++)
  {
    if(i%j==0)
    break;
   }
}
like that???

---

### Post by muteXe on 2012-09-25
It won't be the last 'correct' element cuz there's 2 for loops.

and stick your code in code blocks please :)

---

### Post by Bachstelze on 2012-09-25
> **Mohan1289 said:**
> Why?
The for-loop is for repeating itself until the conditions are satisfied right?


Yes, and the condition has nothing to do with finding the largest palindrome.

---

### Post by Mohan1289 on 2012-09-25
ummm ok i will try

---

### Post by spjackson on 2012-09-25
As something of an optimisation, when looking for the highest possible answer, it can be much better to start at 999 and count down to 100. When going upwards, you never know you have finished until you've evaluated whether 999 * 999 is palindromic. But when going downwards, suppose 600 * 700 gives you a palindromic number - it doesn't but suppose it does. Any number less than 420 is not worth considering because 420 * 999 < 420000. If you follow this reasoning through, you may be able to dramatically reduce the number of loop iterations.

---

### Post by GeneralZod on 2012-09-25
That was very silly of me; ignore :)

---

### Post by The Cog on 2012-09-25
> **GeneralZod said:**
> Alternatively, 

```

    for(int i = 999; i >= 100; i--)
    {
        for(int j = i; j >= 100; j--)
        {
            int product = i * j;


```

should (I think) generate all products of two three-digit numbers, in non-increasing order, so you can stop at the first palindrome.
I'm not convinced of that. It will try 999*100 before trying 998*998. 

But you can certainly break the inner loop as soon as you find a product smaller than the greatest found palindrome - each run of the inner loop will produce decreasing products.

---

### Post by trent.josephsen on 2012-09-25
You may be able to do slightly better than that.

Since i is strictly decreasing and you're only interested in products that are greater than the last palindrome, every palindrome you find establishes a new *lower* bound for j (since if j ever became smaller, you'd have to increase i to increase the product). You can use this lower bound to break the inner loop without first computing the product. The loop will run (probably) more times, but take less time per iteration.

I was bored, so I wrote some Perl to test both algorithms against each other.

fpalin-1.pl:
```
#!/usr/bin/perl
use strict;
use warnings;

use Limits;

my $palin = 0;

LARGER: # this loop iterates over the larger number, $i
for (my $i = $Limits::MAX; $i >= $Limits::MIN; $i--) {
	SMALLER: # this loop iterates over the smaller number, $j
	for (my $j = $i; (my $p = $i*$j) > $palin and $j >= $Limits::MIN; $j--) {
		if ($p eq reverse $p) {
			print "FOUND $i * $j = $p\n";
			$palin = $p;
			next LARGER; # skips a redundant calculation and comparison
		}
	}
}
print "Largest palindrome is $palin.\n";
```

fpalin-2.pl:
```
#!/usr/bin/perl -w
use strict;

use Limits;

my $palin = 0;
my $lbound = $Limits::MIN - 1;

LARGER: # this loop iterates over the larger number, $i
for (my $i = $Limits::MAX; $i > $lbound; $i--) {
	SMALLER: # this loop iterates over the smaller number, $j
	for (my $j = $i; $j > $lbound; $j--) {
		my $p = $i * $j;
		if ($p eq reverse $p) {
			print "FOUND $i * $j = $p\n";
			$lbound = $j;
			$palin = $p if $p > $palin;
			next LARGER; # skips a redundant calculation and comparison
		}
	}
}
print "Largest palindrome is $palin.\n";
```

Limits.pm is as follows (I had to use six-digit numbers to measure the time difference):

```
$Limits::MAX = 999999;
$Limits::MIN = 100000;
```

And I tested as follows:
```
% time ./fpalin-1.pl
FOUND 999999 * 999001 = 999000000999
Largest palindrome is 999000000999.
./fpalin-1.pl  0.53s user 0.00s system 99% cpu 0.536 total
% time ./fpalin-2.pl
FOUND 999999 * 999001 = 999000000999
Largest palindrome is 999000000999.
./fpalin-2.pl  0.28s user 0.01s system 99% cpu 0.288 total
```

That's only two data points, but it's typical of my results. So comparing j against its lower bound approximately cut the time in half over comparing the product against the last palindrome, for this range of numbers.

"For this range of numbers" is the operative phrase, because the results varied widely. For 7 digit numbers the improvement was only about 4%. I did not find any conditions in which my algorithm underperformed the original, but I don't see any reason that should necessarily be the case.

Obviously the relative performance will probably be quite different in other languages, and depend on the method used to test whether a number is a palindrome. I imagine the results would be different in Java, for instance. But I've gone on long enough and probably none of this is very helpful to OP, unless he can already read Perl.

---

### Post by Mohan1289 on 2012-09-26
> **spjackson said:**
> As something of an optimisation, when looking for the highest possible answer, it can be much better to start at 999 and count down to 100. When going upwards, you never know you have finished until you've evaluated whether 999 * 999 is palindromic. But when going downwards, suppose 600 * 700 gives you a palindromic number - it doesn't but suppose it does. Any number less than 420 is not worth considering because 420 * 999 < 420000. If you follow this reasoning through, you may be able to dramatically reduce the number of loop iterations.

Yes you are right. I didn't think of it Thanx For the Advice SPJACKSON

---

### Post by Mohan1289 on 2012-09-26
> **trent.josephsen said:**
> You may be able to do slightly better than that.

Since i is strictly decreasing and you're only interested in products that are greater than the last palindrome, every palindrome you find establishes a new *lower* bound for j (since if j ever became smaller, you'd have to increase i to increase the product). You can use this lower bound to break the inner loop without first computing the product. The loop will run (probably) more times, but take less time per iteration.

I was bored, so I wrote some Perl to test both algorithms against each other.

fpalin-1.pl:
```
#!/usr/bin/perl strict;
use warnings;

use Limits;

my $palin = 0;

LARGER: # this loop iterates over the larger number, $i
for (my $i = $Limits::MAX; $i >= $Limits::MIN; $i--) {
	SMALLER: # this loop iterates over the smaller number, $j
	for (my $j = $i; (my $p = $i*$j) > $palin and $j >= $Limits::MIN; $j--) {
		if ($p eq reverse $p) {
			print "FOUND $i * $j = $p\n";
			$palin = $p;
			next LARGER; # skips a redundant calculation and comparison
		}
	}
}
print "Largest palindrome is $palin.\n";
```

fpalin-2.pl:
```
#!/usr/bin/perl -w
use strict;

use Limits;

my $palin = 0;
my $lbound = $Limits::MIN - 1;

LARGER: # this loop iterates over the larger number, $i
for (my $i = $Limits::MAX; $i > $lbound; $i--) {
	SMALLER: # this loop iterates over the smaller number, $j
	for (my $j = $i; $j > $lbound; $j--) {
		my $p = $i * $j;
		if ($p eq reverse $p) {
			print "FOUND $i * $j = $p\n";
			$lbound = $j;
			$palin = $p if $p > $palin;
			next LARGER; # skips a redundant calculation and comparison
		}
	}
}
print "Largest palindrome is $palin.\n";
```

Limits.pm is as follows (I had to use six-digit numbers to measure the time difference):

```
$Limits::MAX = 999999;
$Limits::MIN = 100000;
```

And I tested as follows:
```
% time ./fpalin-1.pl
FOUND 999999 * 999001 = 999000000999
Largest palindrome is 999000000999.
./fpalin-1.pl  0.53s user 0.00s system 99% cpu 0.536 total
% time ./fpalin-2.pl
FOUND 999999 * 999001 = 999000000999
Largest palindrome is 999000000999.
./fpalin-2.pl  0.28s user 0.01s system 99% cpu 0.288 total
```

That's only two data points, but it's typical of my results. So comparing j against its lower bound approximately cut the time in half over comparing the product against the last palindrome, for this range of numbers.

"For this range of numbers" is the operative phrase, because the results varied widely. For 7 digit numbers the improvement was only about 4%. I did not find any conditions in which my algorithm underperformed the original, but I don't see any reason that should necessarily be the case.

Obviously the relative performance will probably be quite different in other languages, and depend on the method used to test whether a number is a palindrome. I imagine the results would be different in Java, for instance. But I've gone on long enough and probably none of this is very helpful to OP, unless he can already read Perl.

Wow Thanx josephsen
But since i don't know about PERL i don't understand.
Can i reverse the Numbers of a NUMBER

i mean i have to search the palindrome numbers right?

a=9569
can i do like

if(a==reverse(a))
print a is Palindrome..

like that??

Is there any method in Java which can reverse a number??

That's  where i am stuck at i don't know how to reverse a number..

---

### Post by spjackson on 2012-09-26
> **Mohan1289 said:**
> 
a=9569
can i do like

if(a==reverse(a))
print a is Palindrome..

like that??

Is there any method in Java which can reverse a number??

That's  where i am stuck at i don't know how to reverse a number..
It is possible to reverse the (decimal) digits of a number using a loop and arithmetic operations. However, most people would convert the number to a string. Then the problem will become how to reverse a string. For that, Google will produce either the name of a built-in function for languages that have it or a billion results for how to do it for those languages that don't.

Do I detect Project Euler problem #4?

---

### Post by Mohan1289 on 2012-09-26
> **spjackson said:**
> 

Do I detect Project Euler problem #4?

Yes You are exactly correct i am trying to solve Them i completed 3 but i didn't know the function which reverses the decimals of a number..

I Know what to do but i didn't know how to do....

---

### Post by trent.josephsen on 2012-09-26
I took the easy way because to me, checking if a number is a palindrome is the least interesting part of the problem. "$p eq reverse($p)" (parentheses added for clarity) works because reverse() is a built-in function that reverses a string and eq tests whether two strings are the same. Numbers and strings are interchangeable in Perl, so it doesn't matter that $p is an integer; reverse() implicitly converts it to a string to reverse the characters and eq implicitly converts it to a string to compare against the return value of reverse().

In Java, since you ask, you'd have to do that implicit conversion explicitly instead. It would look something like

```
int n = 556655;                                       // number to test
String s = Integer.toString(i);                       // converted to a string
String r = new StringBuffer(s).reverse().toString();  // reversed
if (r.equals(s)) {
    // n is a palindrome
} else {
    // n is not a palindrome
}
```

I had to use StringBuffer to do the reversal because Java's String doesn't have its own reverse() function.

You can see how Java requires you to be a bit more explicit about what's going on here, and takes more code to do the same operation, than Perl. Formally, you would say Perl is more *expressive* than Java. While this is one reason I like Perl and dislike Java, it's important to keep in mind that *more expressive* is not the same thing as *better*; languages vary and each one has different strengths and weaknesses.

---

### Post by Mohan1289 on 2012-09-27
> **trent.josephsen said:**
> I took the easy way because to me, checking if a number is a palindrome is the least interesting part of the problem. "$p eq reverse($p)" (parentheses added for clarity) works because reverse() is a built-in function that reverses a string and eq tests whether two strings are the same. Numbers and strings are interchangeable in Perl, so it doesn't matter that $p is an integer; reverse() implicitly converts it to a string to reverse the characters and eq implicitly converts it to a string to compare against the return value of reverse().

In Java, since you ask, you'd have to do that implicit conversion explicitly instead. It would look something like

```
int n = 556655;                                       // number to test
String s = Integer.toString(i);                       // converted to a string
String r = new StringBuffer(s).reverse().toString();  // reversed
if (r.equals(s)) {
    // n is a palindrome
} else {
    // n is not a palindrome
}
```

I had to use StringBuffer to do the reversal because Java's String doesn't have its own reverse() function.

You can see how Java requires you to be a bit more explicit about what's going on here, and takes more code to do the same operation, than Perl. Formally, you would say Perl is more *expressive* than Java. While this is one reason I like Perl and dislike Java, it's important to keep in mind that *more expressive* is not the same thing as *better*; languages vary and each one has different strengths and weaknesses.


Yeah you are right about that.

Do i have to convert the Integer to String??

Is that the only way?

I mean i want to reverse a number as an Integer without converting it into String??

Can't java do that??

---

### Post by Vaphell on 2012-09-27
you can do it by hand in 3 lines of code if you want to (try) but using existing methods saves time spent otherwise on figuring out the algorithm.

---

### Post by bouncingwilf on 2012-09-27
Of course you could start your loops at the "top" and decrement. Then the first valid result should be the biggest .


Bouncingwilf

---

### Post by trent.josephsen on 2012-09-27
> **bouncingwilf said:**
> Of course you could start your loops at the "top" and decrement. Then the first valid result should be the biggest .


Bouncingwilf
That's what my fpalin-1.pl does. fpalin-2 outperforms it only by eliminating a single test (and taking advantage of the sparseness of palindromic numbers.)

As for reversing a number without making it a string, I mean, sure, you could do it, and as Vaphell observed it's a pretty simple algorithm, but it's more complex than reversing a string and there's no built-in function for it. (How often would that function come in handy?) Like I said, that wasn't the most interesting part of the problem to me, so I took the most straightforward approach -- use the string functions that are already available.

---

### Post by GeneralZod on 2012-09-27
Another interesting approach might be to generate palindromic numbers themselves in reverse order, and stop at the first one that is non prime.  It's relatively easy to do this: e.g. to generate all (say) 5-digit palindromic numbers, count from 999 down to 100 - the corresponding 5-digit palindromes would then be 99999, 99899 ... 10001 - the formula for going from xyz to xyzyx is quite straightforward.

---

### Post by Mohan1289 on 2012-09-28
> **GeneralZod said:**
> Another interesting approach might be to generate palindromic numbers themselves in reverse order, and stop at the first one that is non prime.  It's relatively easy to do this: e.g. to generate all (say) 5-digit palindromic numbers, count from 999 down to 100 - the corresponding 5-digit palindromes would then be 99999, 99899 ... 10001 - the formula for going from xyz to xyzyx is quite straightforward.

Yes I understand.. But how can i reverse the palindrome numbers in reverse order if i don't know how to reverse them..

I googled for it and i got a logic as vaphell it's 3 lines i think

it's as follows:

[COLOR="Red"]"while(n!=0)
{
reverse=reverse*10;
reverse=reverse+n%10;
n=n/10;
}"
[/COLOR]
It's the Logic i found.
at first i don't understand it at all. It took some time for me to understand the logic.

then as per the problem. i have to reverse every number the loop produces and checks weather the reversed number is equal  to the original number.. if so Number is Palindrome...

As bouncingwilf says i have to come from largest to least 
then i have to compare the results
if the next result is less than previous result then the loop breaks. and the result is the Largest Palindrome number?


Am i right??

Any flaws in the logic???

---

### Post by spjackson on 2012-09-28
> **Mohan1289 said:**
> 
[COLOR="Red"]"while(n!=0)
{
reverse=reverse*10;
reverse=reverse+n%10;
n=n/10;
}"
[/COLOR]
It's the Logic i found.
at first i don't understand it at all. It took some time for me to understand the logic.

then as per the problem. i have to reverse every number the loop produces and checks weather the reversed number is equal  to the original number.. if so Number is Palindrome...

It is pretty easy to test whether that code does the right thing. Have you done that?

Using your algorithm, what is the result if n is 100? Is that what you want it to be?

What is the result of reverse(reverse(n)) a) in the general case and b) when n is 100?

---

### Post by Mohan1289 on 2012-09-28
> **spjackson said:**
> It is pretty easy to test whether that code does the right thing. Have you done that?

Using your algorithm, what is the result if n is 100? Is that what you want it to be?

What is the result of reverse(reverse(n)) a) in the general case and b) when n is 100?

wow jackson  i never thought about that... i found that on google it sounds little promising so i wrote that code....

In General Case it's good but when it's 100 It's dispalying 1 as you suspected...

Is there another way??

---

### Post by spjackson on 2012-09-28
> **Mohan1289 said:**
> wow jackson  i never thought about that... i found that on google it sounds little promising so i wrote that code....

In General Case it's good but when it's 100 It's dispalying 1 as you suspected...

Is there another way??
If the result of reversing is purely a numeric type, then the result cannot distinguish between 001 and 1, irrespective of the algorithm used. Most people would convert to a string and reverse the string.

Purley for the purpose of determining whether a number is palindromic, your algorithm is sufficient. reverse(100) ==> 1. 1 != 100. Therefore 100 is not palindromic, which is the result you want.

---

### Post by Mohan1289 on 2012-09-28
> **spjackson said:**
> If the result of reversing is purely a numeric type, then the result cannot distinguish between 001 and 1, irrespective of the algorithm used. Most people would convert to a string and reverse the string.

Purley for the purpose of determining whether a number is palindromic, your algorithm is sufficient. reverse(100) ==> 1. 1 != 100. Therefore 100 is not palindromic, which is the result you want.

Even so how can i overcome that problem??

Any Suggestions that might help??

---

### Post by trent.josephsen on 2012-09-28
You won't be able to overcome it without dealing in strings. Integers don't keep track of leading zeros.

---

### Post by Vaphell on 2012-09-28
what on earth do you need leading 0s for? it doesn't make sense

4400 - not palindromic
004400 - palindromic? but it's the same number?!

besides your i*j won't ever produce a number with leading 0s, so you can ignore numbers with trailing 0s right off the bat (these are not the numbers you are looking for)


either way - you could do it purely with numbers but you'd need an additional int storing  the number of digits which would help restore missing 0s ( 100 (3) -> 1 (3) -> 100 (3) )

---

### Post by Mohan1289 on 2012-10-01
> **Vaphell said:**
> what on earth do you need leading 0s for? it doesn't make sense

4400 - not palindromic
004400 - palindromic? but it's the same number?!

besides your i*j won't ever produce a number with leading 0s, so you can ignore numbers with trailing 0s right off the bat (these are not the numbers you are looking for)


either way - you could do it purely with numbers but you'd need an additional int storing  the number of digits which would help restore missing 0s ( 100 (3) -> 1 (3) -> 100 (3) )

Yes You are Absolutely Correct Vaphell

---

### Post by smartjazz on 2012-10-01
> **spjackson said:**
> As something of an optimisation, when looking for the highest possible answer, it can be much better to start at 999 and count down to 100. When going upwards, you never know you have finished until you've evaluated whether 999 * 999 is palindromic. But when going downwards, suppose 600 * 700 gives you a palindromic number - it doesn't but suppose it does. Any number less than 420 is not worth considering because 420 * 999 < 420000. If you follow this reasoning through, you may be able to dramatically reduce the number of loop iterations.

-----------------------------------------------------------------------------------------

Yeah I agree with spjackson. It is ok & thanks.:)

---

