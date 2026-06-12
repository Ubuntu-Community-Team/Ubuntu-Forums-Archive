---
title: "[c++] Doing Calculus with C++"
date: 2008-08-20
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-20
Hello,

As many of you know Ive been accused of "re-inventing the wheel" a few times and decided to put a stop to that before i get too far into my program. I'm getting the feeling that C++ has quite a diverse library and as such must have one that is capable of doing advanced calculations such as taking derivatives, summations (sigma), integrals, limits. I have taken a few class' on these topics and know about them and there would be ways to do this (for some cases) but there is one area that i would be confused on.

If we have the equation:

(x=0)sum(&#8734;) {1/(8x)} how would we do that one? If it was not going to &#8734; i would say that a simple for loop could be used but i highlt doubt this could be used.

[php]
for(int x=0;x<&#8734;;x++){
//Infinate loop
}
[/php]

and if we were going to do that it could be rewriten as

[php]
int x = 0;
while (1){
x++;
//again infinate loop
}
[/php]

Thanks for any help
~Cody Woolaver

---

### Post by Zugzwang on 2008-08-20
> **Pyro.699 said:**
> As many of you know Ive been accused of "re-inventing the wheel" a few times and decided to put a stop to that before i get too far into my program. I'm getting the feeling that C++ has quite a diverse library and as such must have one that is capable of doing advanced calculations such as taking derivatives, summations (sigma), integrals, limits. I have taken a few class' on these topics and know about them and there would be ways to do this (for some cases) but there is one area that i would be confused on.

Uuuuh, there are no libraries that do that in this sense. There are of course libraries for matrix manipulation and **numerical approximations** of what you want to do - There might even be some for symbolic computations of similar kind, but normally you would evaluate your expression by hand and put the result into your program. You might use the help of "Maxima" or similar software. But these approaches are *incomplete*, i.e. they cannot evaluate everything you type in. 

BTW: You example resolved to "+infinity", i.e. it doesn't converge. :-)

---

### Post by Pyro.699 on 2008-08-20
actually, it converges onto 0. 1 over Infinity is Infinitely small.

(1/1 = 1; 1/2 = 0.5; 1/3 = 0.33; ...; 1/100 = 0.01)

---

### Post by Pyro.699 on 2008-08-20
To be honest here is the calculation im trying to get done in c++

[IMG]http://upload.wikimedia.org/math/4/f/0/4f0feb251d1976d70f645ee00caa089e.png[/IMG]

Its the BBP method for calculating the nth digit of pi without requiring the nth-1 digit. The formula gets easy until you reach the second summation part.

---

### Post by Zugzwang on 2008-08-20
> **Pyro.699 said:**
> actually, it converges onto 0. 1 over Infinity is Infinitely small.

(1/1 = 1; 1/2 = 0.5; 1/3 = 0.33; ...; 1/100 = 0.01)

Right, but in the original definition you wanted to sum up all the elements, right? You can look it your favourite analysis book that $\sum_{i=0}^{\infty} \frac{1}{i}$ does not converge.

---

### Post by Pyro.699 on 2008-08-20
Sorry, i didn't mean converge i meant approaches -.- i kinda stated that infinity was a set digit 8-)

---

### Post by generalguy on 2008-08-20
For the second sum, you sum until the difference between two successive iterations is smaller than the machine epsilon, or until you have the precision you want.

---

### Post by dwhitney67 on 2008-08-20
Pyro -

When doing numerical computations on a computer, calculator, or even an abacus, the "best" computation that can yielded is one that does not exceed the limits of the system.

In other words, if you have an "El Cheapo" calculator that displays only 4 digits, it would be impossible to compute a value such as 9999 + 1.  The calculator simply cannot display more than 4 digits, thus your result will be zero.

The same with computers; some have 32-bit precision, others 64-bits.  When doing numerical calculation (such as the example you provided), ask yourself as to what precision do you want the answer to go to.

Thus "infinity" is subjective to limits of your system, or to limits of the precision you desire, and can trust, of your computation.

Here's a simple example that will attempt to use the maximum unsigned integer to represent infinity, but will terminate when the desired precision is reached:
[PHP]#include <limits>
#include <iostream>

int main()
{
  double precision = 0.00001;
  double result    = 0.0;

  for ( unsigned int i = 1; i < std::numeric_limits<unsigned int>::max(); ++i )
  {
    double prev_result = result;

    result += 1.0/(double)i;

    if ( (result - prev_result) < precision )
    {
      std::cout << "done iterating, i = " << i << std::endl;
      break;
    }
  }

  std::cout << "The result is: " << result << std::endl;
  return 0;
}[/PHP]

---

### Post by Pyro.699 on 2008-08-20
That makes sence, although the code is a little confusing here is the outupt... what exactly does it mean?

> 
Cody@jolteon ~/c++
$ ./test.exe
done iterating, i = 100000
The result is: 12.0901


---

### Post by dwhitney67 on 2008-08-20
> **Pyro.699 said:**
> That makes sence, although the code is a little confusing here is the outupt... what exactly does it mean?
If I coded the wrong equation than you originally posted, then please accept my apologies.

As for the output, it is the sum of:
1/1 + 1/2 + 1/3 + 1/4 + ... + 1/100000

I hope this equals 12.0901!  I merely accepted the result without actually verifying it.  The '100000' is the last value of 'i' that was used in the loop; it is displayed merely for informational purposes.

---

### Post by Pyro.699 on 2008-08-20
Oh no, that was just an example the real calculation i was looking for was in my second post xD the one with the sigma sign in it.

---

### Post by dwhitney67 on 2008-08-20
Below is a solution to the more complex formula you provided, however I do not believe it works... that is the formula.  The result I get is always zero.
[PHP]#include <cstdlib>
#include <cmath>
#include <limits>
#include <iostream>

int main( int argc, char **argv )
{
  // Usage:  pie [n [infinity]]
  //
  // If command-line args not supplied, assume n = 5 and infinity = 10000.
  //
  const unsigned int n        = (argc > 1 ? atoi(argv[1]) : 5 );
  const unsigned int infinity = (argc > 2 ? atoi(argv[2]) : 10000);

  std::cout << "n        = " << n << "\n"
            << "infinity = " << infinity
            << std::endl;

  unsigned int result = 0;

  for ( unsigned int k = 0; k <= n; ++k )
  {
    result += ((unsigned int)pow(16.0, (double)(n-k)) % (8*k + 1)) / (8*k + 1);
  }


  for ( unsigned int k = n+1; k < infinity; ++k )
  {
    result += ((unsigned int)pow(16.0, (double)(n-k)) / (8*k + 1));
  }

  std::cout << "Result   = " << result << std::endl;

  return 0;
}[/PHP]

---

### Post by PandaGoat on 2008-08-20
There are various methods to compute things such as infinite series.  First you should check if it converges: [http://en.wikipedia.org/wiki/Series_(mathematics)#Convergence_criteria](http://en.wikipedia.org/wiki/Series_(mathematics)#Convergence_criteria) and [http://en.wikipedia.org/wiki/Series_(mathematics)#Convergence_tests](http://en.wikipedia.org/wiki/Series_(mathematics)#Convergence_tests).  This book appears fairly good: [http://books.google.com/books?id=IcnIWqUMFEgC&pg=PA103&lpg=PA103&dq=C%2B%2B+infinite+series&source=web&ots=IF4ULBNrvU&sig=70Yk_NZRf43k7cv_pxR_V2ti-3M&hl=en&sa=X&oi=book_result&resnum=3&ct=result#PPA103,M1](http://books.google.com/books?id=IcnIWqUMFEgC&pg=PA103&lpg=PA103&dq=C%2B%2B+infinite+series&source=web&ots=IF4ULBNrvU&sig=70Yk_NZRf43k7cv_pxR_V2ti-3M&hl=en&sa=X&oi=book_result&resnum=3&ct=result#PPA103,M1). Of course after you start computing infinite series, you can move to integrals and stuff easily.  But doing infinite series requires limits.  In fact, calculus is based on limits.  Consider implementing limits before you do series or anything else.

---

### Post by Pyro.699 on 2008-08-20
How do you compute the sum of an infinite series?

---

### Post by Npl on 2008-08-20
> **Pyro.699 said:**
> How do you compute the sum of an infinite series?
*)You solve it analytically (not always possible)
*)You are Chuck Norris
or
*)You compute aslong till you reach your required precision.

Im not familar with the algorithm you posted, but if you look at the second term you can say it will be smaller than 1/15 in any case. Considering the formula should return integer values between 0-9, this would mean you could get away by calculating the first term and then just round up to the next integer.

---

### Post by Pyro.699 on 2008-08-20
It will return a hexadecimal value 0-15 and im prety sure that wont work and will cause some offset after the 10 billionth digit ;)

---

### Post by dwhitney67 on 2008-08-20
> **Pyro.699 said:**
> It will return a hexadecimal value 0-15 and im prety sure that wont work and will cause some offset after the 10 billionth digit ;)
Huh?  Hex value from 0-15?  You mean 0-F, right?  What does this have to do with your OP???

---

### Post by Pyro.699 on 2008-08-20
The BBP Calculus method will return a value of n in hexadecimal

> 
The formula yields an algorithm for extracting [hexadecimal]("http://en.wikipedia.org/wiki/Hexadecimal") digits of &#960;. In order to perform digit extraction first we must rewrite the formula as

> 
This algorithm computes &#960; without requiring custom data types having thousands or even millions of digits. The method calculates the *n*th digit *without* calculating the first *n* &#8722; 1 digits, and can use small, efficient data types.
 The algorithm is the fastest way to compute the *n*th digit (or a few digits in a neighborhood of the *n*th), but &#960;-computing algorithms using large data types remain faster when the goal is to compute all the digits from 1 to *n*.



> 
Now to complete the calculation you must apply this to each of the four sums in turn. Once this is done, take the four summations and put them back into the sum to &#960;.



All this was taken from [Wikipedia](http://en.wikipedia.org/wiki/Bailey%E2%80%93Borwein%E2%80%93Plouffe_formula). My main question of topic is that i need to figure out how i can do this calculus problem with C++ and return that value.


Thanks
~Cody Woolaver

---

### Post by Npl on 2008-08-20
> **Pyro.699 said:**
> It will return a hexadecimal value 0-15 and im prety sure that wont work and will cause some offset after the 10 billionth digit ;)0-15 then. Im fairly certain you can just ignore the second term and it might be even necessary as I cant see how the algorithm could spit out 0 otherwise.

---

### Post by Pyro.699 on 2008-08-20
Well im sure that the second term is there for a reason because i dont see why it would be there and have no effect on the number at all. If that was so then the output from the second term should ALWAYS be zero, which i dont think it would be.

---

### Post by Npl on 2008-08-20
Its called a residual Term and commonly used in approximations. See, as far as I understand you are calculating pi*16^n with the whole formula, which is an irrational number. You thus need to round down to get the nth "Hexadecimal" alone. It makes no sense figuring out formulas noone can compute (the second term is such).
The second term **never** will be zero

---

