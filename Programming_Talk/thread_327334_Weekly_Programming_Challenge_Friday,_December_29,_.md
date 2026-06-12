---
title: "Weekly Programming Challenge: Friday, December 29, 2006"
date: 2006-12-29
forum: Programming Talk
---

### Post by Verminox on 2006-12-29
It's time for the next weekly challenge and jayemef has picked me to set it up so here goes...

I've made this challenge by putting together 2-3 small ideas that I got because I thought they would be very simple individually.

**The Task**:

1. _Reducing a fraction_

(a) Your input will be a floating number. You have to convert it into fraction form and reduce the fraction in the form Numerator/Denominator in its lowest reducable form.

eg. Input: 0.3 ; Output: 3/10
eg. Input  1.8 ; Output: 9/5

(b) Same as above, but instead of a floating number you will given a numerator and denominator as input which is not in reduced form, you have to reduce it.

eg. Input: 121 99 ; Output: 11/9

The two are basically the same thing, but (a) requires converting a float to a fraction.... but in that case you always have a power of 10 as the denominator so part (b) will take care of generalizing it for all pairs of numerator/denominator.


2. _The Prime Test_

Since the above seemed simple, I decided to extend it a bit. Once you find the reduced fraction for either part (a) from a float or for part (b) from a given pair of Numerator and Denominator...... you have to check if the sum of the numerator and denominator is a prime number or not.

eg. If your fraction in reduced form is 3/10, the sum is 3+10 = 13 which is prime, but if the fraction is 11/9, then 11+9=20 is not prime. You have to output the boolean result.


I don't know if any language has any function built in for either of these... but for those who dont.... try not to get the help of external libraries for isPrime() functions, etc.

Not sure what the criteria will be for the winner (definitely not lines of code).... but optimized code (for runtime) and fewer dependencies on external libraries will score more points.

Cheers.

---

### Post by jblebrun on 2006-12-29
> **Verminox said:**
> It's time for the next weekly challenge and jayemef has picked me to set it up so here goes...

I've made this challenge by putting together 2-3 small ideas that I got because I thought they would be very simple individually.


Here's my shot:


```


##LOOK MA, NO IMPORTS ;-)

test=[]
test.append(.3)
test.append(.17)
test.append(.128)
test.append(.130)
test.append(12)
test.append(0)
test.append(1)
test.append(-1)
test.append(2.5)

def rationalize(decimal):
    #Convert to string and then figure it out
    #Multitplying by 10 a lot increases chance of floating pt error
    power10 = 10**(str(float(abs(decimal)))[len(str(float(abs(decimal))))::-1].find('.'))
    return int(decimal*power10), power10

def intersect(set1, set2):
    #Intersection for sets with repeated elements... only include the repeated element the lesser number of times. 
    #i.e. a=[1,1,2,3] b=[1,3,5]  intersection=[1,3]
    return [(i,set2.remove(i))[0] for i in set1 if i in set2]

def frac_reduce(num, dem):
    fact=reduce(lambda x,y: x*y, [1]+intersect(prime_factors(num),prime_factors(dem)))
    return num/fact,dem/fact

def isprime(num):
    return len(prime_factors(num))==1

def prime_factors(num):
    #Brute force-ish. I know there are better algorithms, but I don't remember them. 
    #Anyway, looking up the answer is boring. 
    num=int(abs(num))
    if num < 2:
	return []
    for i in xrange(2,num/2):
	if float(num)/i == num/i:
	    return [i]+prime_factors(num/i)
    return [num]

def num_dem_sum_prime(num, dem):
    return isprime(num+dem)

if __name__=="__main__":

    for i in test:
	rat=rationalize(i)
	red=frac_reduce(*rat)
	ndsp=num_dem_sum_prime(*red)
	print "Number: ",i
	
	print "Rationalized:",rat[0],"/",rat[1]
	print "Reduced:",red[0],"/",red[1]
	print "Num+Dem of reduction is prime?:",ndsp
	print


```

---

### Post by ghostdog74 on 2006-12-29
```


from math import sqrt
def gcd(a, b): 
 	while a: 
 		 a, b = b % a, a 
  	return b 

def prime(num):    
    if num == 1:
	return False
    for i in range(2, int(sqrt(num)) + 1):
	if num % i == 0:
	    return False
    return True 


# reducing fraction  
input = "1.8"
splitted=input.split(".")
left,right = int(splitted[0]), int(splitted[-1])
mult = int("1" + "0" * len( str(right)) )
adder =  (mult * left )  + right
common = gcd(mult,adder)
if common > 1:	
	print "Fraction reduction: %s/%s" % ( str(adder/common) , str(mult/common) )
else:
	print "Fraction: %s /%s" %(adder,mult)

## Prime test example
first = 121
second = 99
todiv = gcd(121,99)
print "Fraction: %s/%s" % ( str(first/todiv) , str(second/todiv) )

print prime( first + second )


```

output:
```

> python test.py
Fraction reduction: 9/5
Fraction: 11/9
False

```

---

### Post by Verminox on 2006-12-29
> **jblebrun said:**
> 
##LOOK MA, NO IMPORTS ;-)

Classic :) ... But I don't think your code is complete :\ ... is it? It ends so abruptly with a print :???: 

I don't know much of Python but ghostdog's entry was good, ... I don't understand how the gcd(a,b) function works though :-k

---

### Post by ghostdog74 on 2006-12-29
> **Verminox said:**
> Classic :) ... But I don't think your code is complete :\ ... is it? It ends so abruptly with a print :???: 

I don't know much of Python but ghostdog's entry was good, ... I don't understand how the gcd(a,b) function works though :-k

I added some print statements
```

>>> def gcd(a, b): 
... 	while a: #until a reaches 0
... 		a, b = b % a, a  #assign remainder to a
... 		print "a, ", a , ":  b, " , b
... 	return b
... 
>>> gcd ( 18, 10)
a,  10 :  b,  18
a,  8 :  b,  10
a,  2 :  b,  8
a,  0 :  b,  2

```

---

### Post by smartbei on 2006-12-29
> **Verminox said:**
> Classic :) ... But I don't think your code is complete :\ ... is it? It ends so abruptly with a print :???: 

I don't know much of Python but ghostdog's entry was good, ... I don't understand how the gcd(a,b) function works though :-k

The easiest way to find the greatest common denomenator is to keep subtracting the smaller number from the greater number until you get to a point where they are both equal or they can be divided with no remainder. For example:
```
gcd(25,35)
```
```
it would do : 35%25 = 10  so: a=10, b=25;
then: 25%10 = 5 so: a=5 b=10;
then: 10%5 = 0 so: a=0 , b=5;
```
so it returns b since a now evaluates to false. I hope that was clear...

---

### Post by amo-ej1 on 2006-12-29
A C implementation, a little rough on the edges (it could use some abs() and such), but works as a proof of concept on nice numbers (nonnegative and both > 0). It uses Euclids algorithm to find the gcd (greatest common divisor).

Then is does an iterative search to find if the number is a prime number. The solution start from b, so it read the nominator and the denominator.
```

#include <stdlib.h>
#include <stdio.h>

int isPrime(int n){
  if(n<2) return 0;
  if(n==2) return 1;
  int cur=2;
  while(cur*cur < n && n%cur!=0){
    cur++;
  }
  return n%cur!=0;
}


int gcd(int a, int b){
  int remain;
  while(b!=0){
    remain=a%b;
    a=b;
    b=remain;
  }
  return a;
}


int main(int argc, char **argv){
  int a,b,curGcd;
  printf("Enter a and b\n");
  scanf("%d %d",&a,&b);
  curGcd = gcd(a,b);
  printf("%d/%d\n", a/curGcd,b/curGcd);
  printf("%d is", a+b);
  if(isPrime(a+b)){
    printf(" prime\n");
  }else{
    printf(" not prime\n");
  }
  return 0;
}

```

Another faster way to find the primes would be by using a probabilistic method such as the Fermat test.

Edit: oh and in order to do the prime test on the reduced fraction you should change:

```

  curGcd = gcd(a,b);
  printf("%d/%d\n", a/curGcd,b/curGcd);
  printf("%d is", a+b);

```

into 

```

  curGcd = gcd(a,b);
  a=a/curGcd;
  b=b/curGcd;
  printf("%d/%d\n", a,b);
  printf("%d is", a+b);

```

---

### Post by Verminox on 2006-12-29
ghostdog, smartbei: I knew the algorithm just didn't undertand the Python code when I first looked at it (mainly because I don't know Python). Thanks though :)

amo-ej1: Good C implementation, though you didn't do the floating number part. I want to see the different methods people use for that :p

---

### Post by gpolo on 2006-12-29
simple solution for week challenge in C

```

/* week challenge - 29/dec/2006
 * -- Guilherme H. Polo Goncalves <ggpolo@gmail.com> */

#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int gcd(int, int);
int nprime(int );

int main(int argc, char *argv[])
{
    int i = 0, frac = 0, divisor, nnumber, div_by, sum, p_check;
    float number;

    if (argc < 3) {
        printf("Usage: %s a float or, %s b int int\n", argv[0], argv[0]);
        return 0;
    } else {
        switch (argv[1][0]) {
            case 'a': 
                while ((argv[2][i] != '.') && (argv[2][i] != '\0'))
                    i++;
                /* count fractional digits */
                while (argv[2][i] != '\0') {
                    i++;
                    frac++;
                }
                frac--;

                number = atof(argv[2]);
                divisor = 1;
                for (i = 0; i < frac; i++) {
                    number *= 10;
                    divisor *= 10;
                }
                nnumber = (int)number;
                break;
            case 'b':
                if (argc < 4) {
                    printf("Invalid usage\n");
                    return 0;
                }

                nnumber = atoi(argv[2]);
                divisor = atoi(argv[3]);
                break;
            default:
                printf("Invalid usage\n");
                return;
        }
    }
    div_by = gcd(nnumber, divisor);
    nnumber = nnumber / div_by;
    divisor = divisor / div_by;
    printf("%d/%d\n", nnumber, divisor);
    sum = nnumber + divisor;
    if (nprime(sum))
       printf("True\n");
    else
        printf("False\n");
    return 0;
}

int gcd(int a, int b)
{
    while(1) {
        a = a % b;
        if (a == 0)
            return b;
        b = b % a;
        if (b == 0)
            return a;
    }
}

int nprime(int n)
{
    int i;

    for(i = 2; i < sqrt(n); i++) {
        if (n%i == 0)
            return 0;
    }
    return 1;
}

```

---

### Post by daz4126 on 2006-12-29
In Ruby I have extended the Integer class to have a gcd method. This uses Euclid's algorithm to find the greatest common divisor (or highest common factor as we say in the Uk!) of a number and another number.

```
class Integer
 def gcd(number)
  a,b = self,number
  until b==0 do
  a,b = b,a%b
  end
 a
 end
end
```

I then added a .to_fraction method to the Float class that uses the previous gcd method to cancel the fraction down:

```
class Float
 def to_fraction
  integer_part = self.to_s.split(".")[0]
  decimal_part = self.to_s.split(".")[1]
  denominator = 10 ** decimal_part.length
  numerator = integer_part.to_i * denominator + decimal_part.to_i
  gcd = numerator.gcd(denominator)
  if gcd > 1
   numerator = numerator/gcd
   denominator = denominator/gcd
  end
  puts numerator + "/" + denominator
 end
end
```

I can also use the gcd method to write a quick program that asks you for a fraction in the form 12/34 and cancels it down into its lowest terms for you.

```
puts "Please enter a fraction in the form a/b"
fraction = gets.chomp
numerator = fraction.split("/")[0]
denominator = fraction.split("/")[1]
gcd = numerator.to_i.gcd(denominator.to_i)
if gcd > 1
   numerator = numerator/gcd
   denominator = denominator/gcd
end
puts "Your fraction in its lowest terms is: " + numerator + "/" + denominator
```

I'm only starting out at Ruby, so I hope that these examples are okay. These programming challenges are really helping me to improve my skills and make me think, they are great fun, thanks for all the contributions.

Happy New Year everybody!

DAZ

---

### Post by Wybiral on 2006-12-29
HTML/javascript...

```

<html>
<body bgcolor = "#7777AA">
<center>
	<b>Weekly Programming Challenge: Friday, December 29, 2006</b><br><br>
	<table border=2 cellpadding="5px" style="text-align: center">
	<td><input type = "button" value = "Reduce from real" onclick = "javascript:reducereal()"></td>
	<td>Real: <input type = "text" id = "real"></td><tr>
	<td><input type = "button" value = "Reduce from fraction" onclick = "javascript:reduce()"></td>
	<td>Fraction: <input type = "text" id="numerator"> / <input type = "text" id="denominator"></td>
	</table><br>
	<input type = "button" value = "is sum of numerator and denominator prime?" onclick = "javascript:prime()">
</center>
</body>
<script language="javascript">
function reducereal() {
	var sLeftRight=real.value.split(".");
	if(sLeftRight[0]==""){sLeftRight[0]="0";};
	nLeft=parseInt(sLeftRight[0]);
	nRight=parseInt(sLeftRight[1]);
	nPlace=parseInt(sLeftRight[1].length);
	denominator.value=Math.pow(10,nPlace);
	numerator.value=nRight + nLeft*parseInt(denominator.value);
	reduce();
}
function reduce() {
	var temp=0;
	var a=Math.abs(numerator.value);
	var b=Math.abs(denominator.value);
	if(a==0 || b==0){alert("Inproper fraction!"); return 0;}
	if(b>a) {temp=a; a=b; b=temp; temp=0;};
	while(!temp) {
		a%=b; if(a==0){temp=b;};
		b%=a; if(b==0){temp=a;};
	};
	numerator.value/=temp;
	denominator.value/=temp;
	real.value=numerator.value/denominator.value;
}
function prime() {
	var response=" is prime!";
	var num = parseInt(numerator.value)+parseInt(denominator.value);
	for (var i=2;i<num;i++) {if (num%i==0) {response=" is NOT prime!"; break;}}
	alert(num+response);
} 
</script>
</html>

```

Save that as "something.html" and open it in your web browser. (Doesn't do well with negative reals, but works with everything else)

---

### Post by jblebrun on 2006-12-29
[QUOTE=Verminox;1942830]Classic :) ... But I don't think your code is complete :\ ... is it? It ends so abruptly with a print :???: 

Yes, it's complete. The ending print just prints a blank line to seperate the printout from each of the unit tests, so that the results are easier to see. You can test any value you want by adding
test.append(<number>) at the top of the file. Be careful, since I don't implement any type checking, it will do dumb things if you don't give it a float or integer.

---

### Post by jblebrun on 2006-12-29
> **Wybiral said:**
> HTML/javascript...


Save that as "something.html" and open it in your web browser. (Doesn't do well with negative reals, but works with everything else)

Oops, you just reminded me that I forgot to handle negative numbers!

[COLOR="Red"]Edit: I fixed the code in the original post.[/COLOR]

---

### Post by jblebrun on 2006-12-29
> **daz4126 said:**
> In Ruby I have extended the Integer class to have a gcd method. This uses Euclid's algorithm to find the greatest common divisor (or highest common factor as we say in the Uk!) of a number and another number.

...

I'm only starting out at Ruby, so I hope that these examples are okay. These programming challenges are really helping me to improve my skills and make me think, they are great fun, thanks for all the contributions.

Happy New Year everybody!

DAZ

Nice ruby code!

---

### Post by jblebrun on 2006-12-29
We still need to see a Lisp/Scheme version, and an assembly version! Who's writing the one that will run on Lego mindstorms? :-D. I want to see an implementation on a Z80, too!

---

### Post by Mirrorball on 2006-12-30
C++ without cmath:

```

#include <iostream>
#include <string>

using namespace std;

class Fraction
{
    public:
        Fraction(const string& number);
        Fraction(int numerator, int denominator);
        int getNumerator() { return num; }
        int getDenominator() { return den; }
        bool isSumPrime();
    private:
        void reduce();
        int num;
        int den;
};

ostream& operator<<(ostream& os, Fraction& f);
int gcd(int a, int b);
bool prime(int x);

int main()
{
    Fraction f1(121, 99);
    cout << f1 << endl;
    cout << f1.isSumPrime() << endl;
    Fraction f2("0.3");
    cout << f2 << endl;
    Fraction f3("1.8");
    cout << f3 << endl;
    Fraction f4(-121, 99);
    cout << f4 << endl;
    Fraction f5("-1.8");
    cout << f5 << endl;
    Fraction f6(2, 1);
    cout << f6 << endl;
    cout << f6.isSumPrime() << endl;
    return 0;
}

Fraction::Fraction(const string& number)
{
    int sign = 1;
    bool decimal = false;
    num = 0;
    den = 1;
    for (string::const_iterator i = number.begin(); i != number.end(); i++) {
        switch(*i) {
            case '-':
                sign = -1;
                break;
            case '.':
                decimal = true;
                break;
            default:
                if(decimal) {
                    den *= 10;
                }
                num = 10 * num + (*i) - '0';
        }
    }
    num *= sign;
    reduce();
}

Fraction::Fraction(int numerator, int denominator)
    : num(numerator), den(denominator)
{
    reduce();
}

bool Fraction::isSumPrime()
{
    return prime(num + den);
}

void Fraction::reduce()
{
    int div = gcd(num, den);
    num /= div;
    den /= div;
}

ostream& operator<<(ostream& os, Fraction& f)
{
    os << f.getNumerator() << "/" << f.getDenominator();
    return os;
}

int gcd(int a, int b)
{
    while (a) {
        int temp = a;
        a = b % a;
        b = temp;
    }
    return b;
}

bool prime(int x)
{
    if (x < 2) {
        return false;
    }
    for (int i = 2; i * i <= x; i++) {
        if (x % i == 0) {
            return false;
        }
    }
    return true;
}

```

The output is:
```

11/9
0
3/10
9/5
-11/9
-9/5
2/1
1

```

---

### Post by amo-ej1 on 2006-12-30
@Mirrorbal:

```

    for(int i = 2; i <= x / 2; i++) {

```

Will look nicer when using sqrt(x) as a boundary :)

Edit: and if you don't want to used cmath, used i*i<x ;)

---

### Post by slavik on 2006-12-30
my perl solution:
```

#!/usr/bin/perl

isprime($n);
primetest($a,$b);

sub isprime {
	my $n = shift;
	return 0 if ($n <= 1);
	for ($i=2;$i<=sqrt(abs($n));$i++) {
		if (int($n%$i)==0) {
			return 0;
		}
	}
	return 1;
}

sub primetest {
	my $a = shift;
	my $b = shift;
	if (isprime($a+$b) == 1) {
		print "Sum of ",$a," and ",$b," is ",$a+$b," which is a prime!\n";
	}
	else {
		print "Sum of ",$a," and ",$b," is ",$a+$b," which is NOT a prime!\n";
	}
}
################# PART 1A ######################

$float = shift;

$num = int($float/1);
$den = 1;

$ans = abs($num/$den);

while ($ans != abs($float)) {
	if ($ans < abs($float)) {
		$num+=1;
	}
	else {
		$den+=1;
	}
	$ans = abs($num/$den);
}

if ($float < 0) {
	$num=-$num;
}

print $float," is ",$num,"/",$den,"\n";

primetest($num,$den);

############### PART 1B #########################

$num = shift;
$den = shift;

if ($num==0 || $den==0) { exit; }

print "$num/$den reduced is: ";

if (int($num%$den)==0) {
	$num/=$den; $den=1;
	primetest($num,$den);
	print "$num/$den\n";
	exit;
}
elsif (int($den%$num)==0) {
	$den/=$num; $num=1;
	print "$num/$den\n";
	primetest($num,$den);
	exit;
}

while (isprime($num)!=1 && isprime($den)!=1 && $num!=1 && $den!=1) {
	if ($num<$den) {
		$min=$den;
	}
	else {
		$min=$num;
	}

	for($i=$min-1;$i>1;$i--) {
		if (int($den%$i)==0 && int($num%$i)==0) {
			$den/=$i;
			$num/=$i;
		}
	}
}

print "$num/$den\n";

primetest($num,$den);

```

please note that the function primetest() is the solution to Part 2.

---

### Post by Mirrorball on 2006-12-31
> **amo-ej1 said:**
> Edit: and if you don't want to used cmath, used i*i<x ;)
Thanks! I will edit my post.

---

### Post by cgrebeld on 2007-01-01
Haskell solution was pretty painless:

```

import Ratio 

-- helper: print a rational number in required format
printRational r = (show $ numerator r) ++ "/" ++ (show $ denominator r)

-- helper: read a fraction from console
readFraction = do
    num <- readLn :: IO Integer
    den <- readLn :: IO Integer
    return (num % den)

-- Part 1 (a): read in a float and print a ratio approximation
getFraction = do
    userIn <- readLn :: IO Double
    putStr $ printRational $ toRational userIn 

-- Part 1 (b): read a ratio and print its reduced form, Ratio class already 
-- does this by default.
reduceFraction = do
    frac <- readFraction
    putStr $ printRational frac 

-- Part 2: Check if num + den is prime
-- There is tons of room for optimizations here

isRatioSumPrime = do
    frac <- readFraction
    putStr $ show $ isPrime ((numerator frac) + (denominator frac))

isPrime 2 = True -- special case, not caught by above code
isPrime n = trialByDiv (primesTo10000 ++ [10001,10003..]) n

-- q < p => p > sqrt n
trialByDiv ps n = doTrialByDiv ps
	where doTrialByDiv (p:ps) = let (q,r) = n `quotRem` p in if r == 0 then False else if q < p then True else doTrialByDiv ps
	      doTrialByDiv [] = True

-- precalculate the primes up to 1000 for efficiency
primesTo100 :: [Integer]
primesTo100 = [2,3,5,7,11,13,17,19,23,29,31,37,41,43,47,53,59,61,67,71,73,79,83,89,97]
primesTo10000 = primesTo100 ++ filter (trialByDiv primesTo100) [101,103..9999]  


```

---

### Post by mat087 on 2007-01-01
In C++ :

```

#include <string>
#include <utility>
#include <sstream>
#include <cmath>

typedef std::pair<int, int> fraction_t;

int GreatestCommonDivisor( int a, int b )
{
     int c;
     while( b != 0 )
     {
          c = b;
          b = a % b;
          a = c;
     }
     return a;
}

bool IsPrime ( const int Number )
{
     if( Number == 2 )
          return true;
     
     if( Number % 2 == 0 || Number < 2 )
          return false;
     
     int UpperLimit = static_cast<int>( sqrt(Number) + 1 );
     
     for(int i = 3; i < UpperLimit; i += 2)
     {
          if( Number % i == 0 )
               return false;
     }
     return true;
}

fraction_t ReduceFraction( const fraction_t Fraction )
{
     int Gcd = GreatestCommonDivisor( Fraction.first, Fraction.second );
     return fraction_t( Fraction.first / Gcd, Fraction.second / Gcd );     
}

int GetDecimalPart( const float DecimalPart, int & DecimalLength )
{
     if( !DecimalPart )
     {
          DecimalLength = 0;
          return 0;
     }
     
     std::stringstream s, s2;
     int IntDecimalPart;

     s << DecimalPart;
     s2 << s.str().substr( 2, s.str().length() );
     s2 >> IntDecimalPart;
     DecimalLength = s2.str().length();
     return IntDecimalPart;
}

fraction_t FloatToFraction( const float Number )
{
     if( !Number )
          return fraction_t( 0, 0 );

     int IntegerPart = static_cast<int>( Number );
     int DecimalLength;
     int DecimalPart = GetDecimalPart( fabs( Number - IntegerPart), DecimalLength );
     
     int DecimalPartDenominator = static_cast<int>( pow(10, DecimalLength) );
     
     if( IntegerPart )
     {
          return ReduceFraction( fraction_t(IntegerPart * DecimalPartDenominator + DecimalPart, DecimalPartDenominator) );
     }
     else if( Number > 0 )
     {
          return ReduceFraction( fraction_t(DecimalPart, DecimalPartDenominator) );
     }
     else
     {
          return ReduceFraction( fraction_t(-DecimalPart, DecimalPartDenominator) );
     }
}

```

Here is the main to test it :

```

#include <iostream>

void DisplayReducedFraction( fraction_t Fraction )
{
     std::cout << Fraction.first << " / " << Fraction.second;
     
     if( Fraction.first >= 0 || Fraction.second >= 0 ) //***
          std::cout << " ( " << IsPrime( Fraction.first + Fraction.second ) << " )" << std::endl << std::endl;
     else
          std::cout << " (0)" << std::endl;
}

int main()
{
     char c;
     fraction_t Fraction;
     float Number;
     
     do
     {
          std::cout << "1. Floating number." << std::endl 
                    << "2. Fraction."        << std::endl
                    << "q. Quit."            << std::endl;
          
          std::cin >> c;
          
          if( c == '1' )
          {
               std::cin >> Number;
               DisplayReducedFraction( FloatToFraction( Number ) );
          }
          else if( c == '2' )
          {
               std::cin >> Fraction.first;
               std::cin >> Fraction.second;
               DisplayReducedFraction ( ReduceFraction( Fraction ) );
          }
     }
     while( c != 'q' );
}

```

***  "if( Fraction.first >= 0 || Fraction.second >= 0 )"
I added this condition because it wasn't specified, if the reduced fraction was negative, which one (numerator or denominator) has the negative sign. So I simply display false.

-5 / 2 => -5 + 2 = -3 => not prime.
5 / -2 => 5 - 2 = 3 => prime.


Mathieu

---

### Post by Verminox on 2007-01-02
> **mat087 said:**
> -5 / 2 => -5 + 2 = -3 => not prime.
5 / -2 => 5 - 2 = 3 => prime.


I always thought that when checking for primes the sign should be ignored. From what I had learnt, (-x) is prime if (x) is a prime.... making -3 also a prime.

---

### Post by Mirrorball on 2007-01-02
I learned that only natural numbers can be primes.

---

### Post by jblebrun on 2007-01-02
Indeed, 

> A prime number (or prime integer, often simply called a "prime" for short) is a positive integer p>1 that has no positive integer divisors other than 1 and p itself. 
([From Mathworld]("http://mathworld.wolfram.com/PrimeNumber.html"))

---

### Post by navinp on 2007-01-02
```

/* Usage examples text in  [ ]needn't be entered from the keyboard 
1 [option 1]
0.8 [input for option 1]
3 [option 3 to tell whether number is prime or not . not necessary]
2 [option 2]
2 11 [input for option 2 ]
3 [option 3 to tell whether number is prime or not . not necessary]


*/
#include<stdio.h>
#include<math.h>
#include<string.h>
int gcd(int m, int n)
{
	if (m % n == 0)
		return n;
	return gcd(n, m % n);
}

int isprime(int k)
{
	int i, z;
	if (k == 2)
		return 1;
	z = sqrt(k);
	if (k % 2 == 0)
		return 0;
	for (i = 3; i <= z; i += 2)
		if (k % z == 0)
			return 0;

	return 1;
}

void print(void)
{
	printf("Enter 1  for 1a\n");
	printf("Enter 2 for 1b\n");
	printf("Enter 3 for 2\n");
	printf("Any other option breaks\n");
	printf("please note option 3 can be used only after selecting either option1 or option 2\n");
}

int main()
{
	char str[20];
	int len, i, z, k, u, v, num, opt, flag = 0;

	print();
		flag = 0;
	while (scanf(" %d", &opt) != EOF) {
		if (opt == 1) {
			flag = 1;
			scanf(" %s", str);
			len = strlen(str);
			for (i = 0; i < len; i++)
				if (str[i] == '.') {
					break;
				}
			if (i == len || i == len - 1)
				printf("%s/1\n", str);
			else {
				// 1.33
				z = pow(10, len - i - 1);
				u = strtoul(str + i + 1, NULL, 10);
				str[i] = '\0';
				v = strtoul(str, NULL, 10);
				v = v * pow(10, len - i - 1);
				num = v + u;
				k = gcd(num, z);
				if (k > 1)
					printf("%d/%d\n", num / k, z / k);
				else
					printf("%d/%d\n", num, z);
			}
		}
		if (opt == 2) {
			flag = 1;
			scanf(" %d %d", &num, &z);
			k = gcd(num, z);
			if (k > 1)
				printf("%d/%d\n", num / k, z / k);
			else
				printf("%d/%d\n", num, z);
		}
		if (opt == 3) {
			if (flag != 1) {
				printf("no strings entered for fraction\n");
			} else {
				if (isprime(num + z))
					printf("yes\n");
				else
					printf("no\n");
			}

				flag=0;
		}
		if(opt!=1 && opt!=2 && opt!=3)
			break;
		print();
	}

	return 0;
}


```

---

### Post by GeoMX on 2007-01-02
Another C++ version (no classes here :P)

```

#include <iostream>
#include <sstream>
#include <cmath>
using namespace std;

// A fraction
struct Fraction {
	Fraction() { numerator = denominator = 1; }

	int numerator;
	int denominator;
};

// Create a Fraction
Fraction newFraction( float input );
Fraction newFraction( int numerator, int denominator );

// Reduce a Fraction
void reduceFraction( Fraction& fraction );

// Print a Fraction
void printFraction( Fraction& fraction );

// Utility functions
bool prime( int number );
int mcd( int a, int b );

//***  Main program ***
int main() {
	float decimal = 0.3;
	Fraction a = newFraction( decimal );
	cout << decimal << " converted to fraction: "; printFraction( a ); cout << endl;
	reduceFraction( a );
	cout << "In reduced form: "; printFraction( a ); cout << endl;
	int sum = a.numerator + a.denominator;
	cout << "Prime test of fraction a outputs: " << prime( sum ) << endl << endl;

	decimal = 1.8;
	Fraction b = newFraction( decimal );
	cout << decimal << " converted to fraction: "; printFraction( b ); cout << endl;
	reduceFraction( b );
	cout << "In reduced form: "; printFraction( b ); cout << endl;
	sum = b.numerator + b.denominator;
	cout << "Prime test of fraction b outputs: " << prime( sum ) << endl << endl;

	Fraction c = newFraction( 121, 99 );
	cout << "Original fraction: "; printFraction( c ); cout << endl;
	reduceFraction( c );
	cout << "Reduced form: "; printFraction( c ); cout << endl;
	sum = c.numerator + c.denominator;
	cout << "Prime test of fraction c outputs: " << prime( sum ) << endl;

	return 0;
}

Fraction newFraction( float input ) {
	// Convert float to string
	ostringstream os;
	os << input;
	string sNumber = os.str();

	// Get integer and decimal parts
	string integerPart = sNumber.substr( 0, sNumber.find( ".", 0 ) );
	string decimalPart = sNumber.substr( sNumber.find( ".", 0 ) + 1 );

	// Set denominator
	int denominator = 1;
	for ( int i = 0; i < decimalPart.length(); i++ ) {
		denominator *= 10;
	}

	// Set numerator
	int numerator = 0;
	for ( int i = integerPart.length(); i > 0; i-- ) {
		string sDigit = integerPart.substr( integerPart.length() - i, 1 );
		int digit;
		istringstream is( sDigit );
		is >> digit;
		numerator += digit * pow( static_cast<double>( 10 ), i - 1 );
	}
	
	// Add decimals to numerator
	istringstream istream( decimalPart );
	int aux;
	istream >> aux;

	numerator *= denominator;
	numerator += aux;

	return newFraction( numerator, denominator );
}

Fraction newFraction( int numerator, int denominator ) {
	Fraction f;
	
	f.numerator = numerator;
	// Denominator is never 0.
	f.denominator = denominator != 0 ? denominator : 1;

	return f;
}

void reduceFraction( Fraction& fraction ) {
	int common = mcd( fraction.numerator, fraction.denominator );
	fraction.numerator /= common;
	fraction.denominator /= common;
}

void printFraction( Fraction& fraction ) {
	cout << fraction.numerator << "/" << fraction.denominator;
}

bool prime( int number ) {

	for (int i = 2; i < number; i++) {

		if ( number % i == 0) return false;

	}

	return true;

}

int mcd( int x, int y ) {
	if ( y == 0 ) return x;

	else	return mcd( y, x % y );

}

```

I liked the short Haskell version, though it's really hard for me to read :).

Regards,
JJ

---

### Post by mat087 on 2007-01-02
I've always learnt that prime numbers must be > 1. In fact, this is not always true : [http://primes.utm.edu/notes/faq/negative_primes.html](http://primes.utm.edu/notes/faq/negative_primes.html)

Actually, I made this condition "if( Fraction.first >= 0 || Fraction.second >= 0 )" because it was ambiguous ( -2 / 5 => 3; 2 / -5 => -3 ). But, of course, if the sign is ignored, there is no need to test this condition, we might replace it with "IsPrime( abs(Fraction.first + Fraction.second) )" instead.


Mathieu

---

### Post by Verminox on 2007-01-04
Uptil now I liked the ruby implementation  by daz4126 and ghostdog's python implementation the best...

I'm surprised that there are no PHP entries... this would be really short and quick in PHP.

PS: Also, most of you have not tried optimizing the code much.
(1) In the iteration always use (i*i < n) not (i < n) or (i < sqrt(n)).
(2) Don't use (i++) at the end of your loops. All alternate numbers are going to fail the divisor test if 2 fails. Use (i = i+2) to skip even numbers except at the first round when checking with 2 itself.
etc...

---

### Post by slavik on 2007-01-04
> **Verminox said:**
> Uptil now I liked the ruby implementation  by daz4126 and ghostdog's python implementation the best...

I'm surprised that there are no PHP entries... this would be really short and quick in PHP.

PS: Also, most of you have not tried optimizing the code much.
(1) In the iteration always use (i*i < n) not (i < n) or (i < sqrt(n)).
(2) Don't use (i++) at the end of your loops. All alternate numbers are going to fail the divisor test if 2 fails. Use (i = i+2) to skip even numbers except at the first round when checking with 2 itself.
etc...

a=sqrt(n);
for (i=2;i<a;i+=2) {}

that is faster than i*i<n because for larger n, the repeated additions (that is all multiplication is) will grow faster than a single sqrt call.

also, it all depends on how picky you want to be ... because that prime() function is not optimal (the algorithm is not optimal, there are better ones out there).

---

### Post by jblebrun on 2007-01-05
> **Verminox said:**
> Uptil now I liked the ruby implementation  by daz4126 and ghostdog's python implementation the best...

I'm surprised that there are no PHP entries... this would be really short and quick in PHP.

PS: Also, most of you have not tried optimizing the code much.
(1) In the iteration always use (i*i < n) not (i < n) or (i < sqrt(n)).
(2) Don't use (i++) at the end of your loops. All alternate numbers are going to fail the divisor test if 2 fails. Use (i = i+2) to skip even numbers except at the first round when checking with 2 itself.
etc...

Hey, what's wrong with mine? :-P Do you still think it's broken or incomplete? Because it's not...

---

### Post by jblebrun on 2007-01-05
> **Verminox said:**
> Uptil now I liked the ruby implementation  by daz4126 and ghostdog's python implementation the best...

I'm surprised that there are no PHP entries... this would be really short and quick in PHP.

PS: Also, most of you have not tried optimizing the code much.
(1) In the iteration always use (i*i < n) not (i < n) or (i < sqrt(n)).
(2) Don't use (i++) at the end of your loops. All alternate numbers are going to fail the divisor test if 2 fails. Use (i = i+2) to skip even numbers except at the first round when checking with 2 itself.
etc...

Mine's not optimized because I took a different approach by using a prime factorization function to handle both the GCD computation and the prime detection. My point was to highlight the similarity between the two requirements. You can calculate the GCD by dividing by all common prime factors, and a prime number has a prime factorization list length of 1 (itself).

---

### Post by maddog39 on 2007-01-06
I'm a PHP developer. Just having trouble understanding exactly what we need to do. Still a bit confused/stumped with this one.

---

### Post by slavik on 2007-01-06
> **maddog39 said:**
> I'm a PHP developer. Just having trouble understanding exactly what we need to do. Still a bit confused/stumped with this one.
1a. give a floating point number (not a whole number) convert it to a fraction. (.75 => 3/4)
1b. given a fraction, write it in reduced form (10/100 => 1/10)
2. take the output from 1a and/or 1b and find if the sum of the numerator and denominator is a prime number (2/4 => 3+4 => 7 is prime).

speaking of which who is the winner and where is the next contest?

---

### Post by Klipt on 2007-01-06
> **jblebrun said:**
> We still need to see a Lisp/Scheme version
Common Lisp already has a rational type which is automatically reduced and a 'rationalize' function to convert from float, so part 1 is trivial. But here's a tail-recursive prime tester:

```
(defun primep (n)
  (labels ((primep-inner (n test)
	     (cond ((> (* test test) n) t)
		   ((= (mod n test) 0) nil)
		   ((= (mod n (+ n 2)) 0) nil)
		   (t (primep-inner n (+ test 6))))))
    (cond ((< n 2) nil)
	  ((< n 4) t)
	  ((= (mod n 2) 0) nil)
	  ((= (mod n 3) 0) nil)
	  (t (primep-inner n 5)))))
```

After 2 and 3, it only tests divisibility for 2 out of every 6 consecutive numbers, since the other 4 are multiples of 2 or 3.

---

### Post by Verminox on 2007-01-06
> **slavik said:**
> speaking of which who is the winner and where is the next contest?

I picked ghostdog as the winner, because he provided a clean and to the point solution in Python, but he doesn't have any ideas for a next challenge.

If any of you have any ideas go ahead and make the next challenge... just make sure that we dont have 2-3 challenges running around. If no one can think of one till tomorow I'll make one myself.


PS: Should we also start something like a "Monthly programming contest" with bigger projects (not very large, but not snippets either) which we can all try and upload sources/binaries (as the code itself will be considerably large / split over multiple files).

Of course, there won't be anything special for the winner ](*,) but it will still be fun for many people from this forum to work on a project together (but separately) and see how each one's program turns out.

---

### Post by Lster on 2007-01-06
I like the idea of a sqrt calculator that must:
[LIST]
[*]not use sqrt() or exponent
[*]return the answer to 5 significant figures
[*]and print all squareroots
[/LIST]

Just a quick idea,
Lster

---

### Post by tkjacobsen on 2007-01-06
ooups

---

### Post by tkjacobsen on 2007-01-06
> **Lster said:**
> I like the idea of a sqrt calculator that must:
[LIST]
[*]not use sqrt() or exponent
[*]return the answer to 5 significant figures
[*]and print all squareroots
[/LIST]

Just a quick idea,
Lster

I did it quickly in octave...
```

function y=sqrt2(x)
run=true;
init=1;
while run
  init=init*10;
  if init^2 > x
    run=false;
    init=init/10;
  end
end

for dec=0:10
  for i=1:10
    eval = (init+i*init*10^(-dec))^2;
    if eval > x
      init=init+(i-1)*init*10^(-dec);
      break;
    end
  end
end

y=init;

```

---

### Post by Verminox on 2007-01-06
> **Lster said:**
> I like the idea of a sqrt calculator that must:
[LIST]
[*]not use sqrt() or exponent
[*]return the answer to 5 significant figures
[*]and print all squareroots
[/LIST]

Just a quick idea,
Lster


You can just convert that problem to finding the roots of the equation "x^2 - n = 0", where n is the number whose square root is to be found, and then get an accurate answer upto 5 digits in about 3 or 4 iterations of using Newton-Raphson method which I learnt in class last week.... lol finally my classwork makes sense.

A harder problem would be finding the n'th root, or even harder, creating a manual power() function, including floating exponents....

But all these are again "algorithms" which are small snippets. A larger project would be something like maybe a Sudoku solver. I've always wanted to write one but never found the time.

---

### Post by xtacocorex on 2007-01-06
Newton-Raphson is pretty powerful stuff.  I used it in two of my Aerospace programming classes.

I just did the Square Root program in FORTRAN using the Babylonian iterative method because I was bored and I haven't had to program at my job yet.  I doubt I will anytime soon, so I wanted to practice.

---

### Post by Verminox on 2007-01-06
The babylonian iterative method is the same as the Newton-Raphson method. Just that Newton's method is more generalized but when you use the particular equation i posted before you come to the babylonian formula so its basically the same thing.

---

### Post by eteran on 2007-01-09
> **Verminox said:**
> 
I'm surprised that there are no PHP entries... this would be really short and quick in PHP.


Here you go:

[PHP]
#!/usr/bin/php
<?php

/**
 * Programming Challenge 2006/12/29
 * http://www.ubuntuforums.org/showthread.php?t=327334 
 *
 * Task:
 * 1. Reducing a fraction
 * (a) Your input will be a floating number. You have to convert it into
 *     fraction form and reduce the fraction in the form 
 *     Numerator/Denominator in its lowest reducable form.
 *
 *     eg. Input: 0.3 ; Output: 3/10
 *     eg. Input 1.8 ; Output: 9/5
 *
 * (b) Same as above, but instead of a floating number you will given a
 *     numerator and denominator as input which is not in reduced form,
 *     you have to reduce it.
 *
 *     eg. Input: 121 99 ; Output: 11/9
 *
 * The two are basically the same thing, but (a) requires converting a
 * float to a fraction.... but in that case you always have a power of 10
 * as the denominator so part (b) will take care of generalizing it for
 * all pairs of numerator/denominator.
 *
 * 2. The Prime Test
 * Since the above seemed simple, I decided to extend it a bit. Once you
 * find the reduced fraction for either part (a) from a float or for
 * part (b) from a given pair of Numerator and Denominator......
 * you have to check if the sum of the numerator and denominator is a
 * prime number or not.
 *
 * eg. If your fraction in reduced form is 3/10, the sum is 3+10 = 13
 * which is prime, but if the fraction is 11/9, then 11+9=20 is not prime.
 * You have to output the boolean result.
 */
 
// {{{ defines

/*
 * input for task 1a. Must be float
 */ 
define('INPUT_1A', (float) 0.3);
/*
 * input for task 1b. numerator and denominator
 */
define('INPUT_1B_NUM', (int) 121);
define('INPUT_1B_DEN', (int) 99);

// }}}

// {{{ functions

/**
 * float2fraction()
 * 
 * converts a floating point number to the lowest reducable fraction
 *
 * @input  float  $floatInput
 * @return string fraction in the form "numerator/denominator"
 */
function float2fraction($floatInput)
{
	$intDenominator = 1;
	$floatNumerator = $floatInput;
	
	while (ceil($floatNumerator) != $floatNumerator)
	{
		$intDenominator++;
		$floatNumerator = $floatInput * $intDenominator;		
	}
	
	$intNumerator = (int) $floatNumerator;
	
	return $intNumerator ."/". $intDenominator;  
}

/**
 * reduceFraction()
 *
 * reduces numerator, denominator to the lowest reducable form
 *
 * @input  int    $intNumerator
 * @input  int    $intDenominator
 * @return string lowest reducable fraction in the form
 *                "numerator/denominator"
 */
function reduceFraction($intNumerator, $intDenominator)
{
	$floatNumber = (float) $intNumerator / $intDenominator;
	
	return float2fraction($floatNumber);
}

/**
 * isPrime()
 *
 * checks if the given integer is a prime
 *
 * @input  int	$int
 *
 * @return bool
 */
function isPrime($int)
{
	/*
	 * integer lower than two cannot be a prime
	 */	
	if ($int < 2)
	{
		return false;
	}	
	
	/*
	 * two is a prime and a special case
	 */
	if ($int == 2)
	{
		return true;
	}
		
	/*
	 * each prime greater than two has to be odd
	 */
	if (($int % 2) == 0)
	{
		return false;
	}
	
	/*
	 * Eratosthenes Test
	 */
	return isPrimeEratosthenes($int);
}

/**
 * isPrimeEratosthenes()
 *
 * Checks if a given integer is a prime.
 *
 * @see    http://de.wikipedia.org/wiki/Sieb_des_Eratosthenes
 *
 * @input  $int odd unsigned integer, bigger than 2
 *
 * @return bool
 */
function isPrimeEratosthenes($int)
{
	$aryIsPrime = array();
	
	for ($i = 3; $i <= $int; $i++)
	{
		if (($i % 2) == 0)
		{
			$aryIsPrime[$i] = false; 
		}
		else
		{
			$aryIsPrime[$i] = true;
		}
	}
	
	$i = 3;
	while (($i * $i) <= $int)
	{
		if ($aryIsPrime[$i] === true)
		{
			$x = ($i * $i);
			$y = $i;
			
			while ($x <= $int)
			{
				if ($x == $int)
				{
					return false;
				}
				
				$aryIsPrime[$x] = false;
			
				$y++;
				$x = $y * $i;
			}
		}
		
		$i++;
		
		while ($aryIsPrime[$i] === false)
		{
			$i++;
		}
	}
	
	return $aryIsPrime[$int];
}

// }}}

// {{{ main

list($int1aNum, $int1aDen) = split("/", float2fraction(INPUT_1A));
if (isPrime($int1aNum + $int1aDen))
{
	$str1aIsPrime = "true";
}
else
{
	$str1aIsPrime = "false";
}

list($int1bNum, $int1bDen) = split("/", reduceFraction(INPUT_1B_NUM, INPUT_1B_DEN));
if (isPrime($int1bNum + $int1bDen))
{
	$str1bIsPrime = "true";
}
else
{
	$str1bIsPrime = "false";
}

// }}}

// {{{ output

echo "Task 1 (a) - in: ". INPUT_1A ." - out: ". $int1aNum ."/". $int1aDen ." | Task 2 - in: ". ($int1aNum + $int1aDen) ." - out: ". $str1aIsPrime ."\n";
echo "Task 1 (b) - in: ". INPUT_1B_NUM ."/". INPUT_1B_DEN ." - out: ". reduceFraction(INPUT_1B_NUM, INPUT_1B_DEN) ." | Task 2 - in: ". ($int1bNum + $int1bDen) ." - out: ". $str1bIsPrime . "\n";

// }}}

?>
[/PHP]

I could have also used gmp_prob_prime() to determ if the given number is a prime, but I felt its part of the challenge to create an own prime test.

Thanks for the challenge, learnt alot.

---

### Post by 56phil on 2007-01-11
Here's an entry with a couple of twists:[LIST=1]
 [*]it has it's own square root function
[*]it pickles the primes it finds for future runs of the program
[/LIST]
It takes any number of values and evaluates them.  You enter n to get that number's prime factors. n.n to change the decimal into a fraction and n/n to reduce the fraction.
```

#!/usr/bin/python
""" Weekly Programming Challenge: Friday, December 29, 2006 """


import os
import cPickle
import sys


primes = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47, 53, 59]
fn = 'Primes'
fn_used = False
org_p_cnt = len(primes)


def sroot(x):
    a = float(x) / 4
    b = x
    while int(a) != int(b):
        b = x / a
        a = (b + a) / 2
    return int(a) + 1


def nth_prime(n):
    """ gets the next prime 
    
    return number """
    global primes
    global fn
    global fn_used
    global org_p_cnt
    while n >= len(primes):
        if fn_used:
            m = primes[-1] + 2
            while not isprime(m):
                m += 2
            primes.append(m)
        else:
            try:
                fn_used = True
                mpf = open(fn, 'rb')
            except IOError, e:
                print '*** ERROR *** Could not open %s for load.\ne = %s' % (fn, e)
            else:
                primes = cPickle.load(mpf)
                mpf.close()
                org_p_cnt = len(primes)
                print 'Using pickeled primes.'
    return primes[n]


def isprime(n):
    """ tells if n is prime

    return boolean """
    global primes
    if n < 2:
        return False
    if n in primes:
        return True
    limit = int(sroot(n)) + 1
    i = 0
    prime = 2
    while True:
        if prime >= limit:
            return True
        if n % prime == 0:
            return False
        i += 1
        prime = nth_prime(i)


def pf(n):
    """ returns the prime factors of n 
    
    return list  """
    a = []
    if n < 0:
        n = -n
        a.append((-1, 1))
    limit = sroot(n)
    i = 0
    prime = 2
    f_count = 0
    while prime < limit:
        while n % prime == 0:
            n /= prime
            f_count += 1
        if f_count > 0:
            a.append((prime, f_count))
            limit = int(sroot(n)) + 1
            f_count = 0
        i += 1
        prime = nth_prime(i)
    if n > 1:
        a.append((n, 1))
    return a


def reduce(n, d):
    """ reduces a fraction

    return tuple """
    sign = 1
    if n < 0:
        n = -n
        sign = -1
    limit = sroot(min(n, d))
    old_d = d
    i = 0
    prime = 2
    while limit > prime:
        while n % prime == 0 and d % prime == 0:
            n /= prime
            d /= prime
        if old_d != d:
            limit = sroot(min(n, d))
            old_d = d
        i += 1
        prime = nth_prime(i)        
    return (sign*n, d)


def ratio(a):
    """ Handles input strings with a '/' 

    return tuple """
    b = a.find('/')
    n = int(a[:b])
    d = int(a[b+1:])
    if d < 0:
        n = -n
        d = -d
    return reduce(n, d)


def floater(x):
    """ converts x, a float into a ratio of integers

    return tuple """
    k = len(x) - 1
    i = x.find('.')
    return reduce(int(x[:i] + x[i+1:]), 10 ** (k-i))


def prt_lst(a, ans):
    """ prints the result """
    n = ans[0]
    d = ans[1]
    if d == 1:
        print '%s = %d' % (a, n)
    else:
        print '%s = %d/%d' % (a, n, d)


def do_input(a):
    """ handles an input string """
    if a.find('.') >= 0:
        ans = floater(a)
        prt_lst(a, ans)
        x = sum(ans)
        if isprime(x):
            print '%d is prime' % (x)
    elif a.find('/') > 0:
        prt_lst(a, ratio(a))
    elif a.isdigit():
        x = int(a)
        ans = pf(x)
        if len(ans) == 1 and ans[0] == (x, 1):
            print '%d is prime' % (x)
        else:
            print '%s =' % (a),
            while ans:
                b = ans.pop(0)
                if b[1] > 1:
                    print '%d^%d' % (b[0], b[1]),
                else:
                    print b[0],
                if len(ans) > 0:
                    print '*',
            print
    else:
        print "Can't process %s" % (a)

if __name__ == '__main__':
    for s in sys.argv[1:]:
        do_input(s)
    if len(primes) > org_p_cnt:
        try:
            mpf = open(fn, 'w')
        except IOError, e:
            print '*** ERROR *** Could not open %s for dump.\ne = %s' % (fn, e)
        else:
            cPickle.dump(primes, mpf, 2)
            mpf.close()
            print 'Updated pickeled primes. %d primes added.' % (len(primes) - org_p_cnt)


```

---

### Post by daz4126 on 2007-01-11
> **Verminox said:**
> Uptil now I liked the ruby implementation  by daz4126 and ghostdog's python implementation the best...


Thanks for the kind words. I think ghostdog deserved to win though because I didn't do the prime test. This was because I was frantically trying to get an entry in before going skiing over new year and only had access to a ruby interpreter using an interactive online version, so didn't have the time to finish the challenge off which is a shame because it has been my favourite so far.

Now I'm back, I'm interested to read about a monthly challenge, but not sure how many contributions I could make (although just reading other entries is great in itself). Working together and in teams is also a good idea. I think we work together anyway by discussing each others' entries, but how would teams work? Would they be based on language? Team Ruby vs Team Python! That would be fun to see...

I've also been thinking that when testing for primes, you only need to test numbers of the form 6n + 1 and 6n -1 up to the square root of the number (because prime numbers are only of the form 6n + or - 1 and if there isn't a prime factor below the square root, there won't be one above it). This would cut down dramatically on the number of tests that needed doing.

DAZ

---

