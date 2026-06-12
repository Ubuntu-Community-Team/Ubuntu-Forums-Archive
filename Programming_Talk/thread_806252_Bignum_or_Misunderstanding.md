---
title: "Bignum or Misunderstanding?"
date: 2008-05-24
forum: Programming Talk
---

### Post by JupiterV2 on 2008-05-24
I am attempting another Project Euler task. The task is looking for the product of all number below n.

n! = (n*(n-1))*...* 5 * 4 * 3 * 2 * 1

If n = 5 then the result is 5 * 4 * 3 * 2 * 1 = 120

So to me, I did a recursive loop to calculate it. Using small number, the task is trivial. However, the number gets exponentially large and the gnu compiler won't handle numbers larger than unsigned long long int.

if n = 100 then we'd get a massive number (100 * 99 * 98...) well beyond the normal threshold of gcc. Can I store such a large number without relying on an external library?

---

### Post by CptPicard on 2008-05-24
Bits are bits. Sounds like a BigNum exercise. :) Or, use Lisp...

---

### Post by slavik on 2008-05-24
Here's the solution.

[php]
#!/usr/bin/perl

@answer=(1);
$factorial = 100;

for ($i=1;$i<=$factorial;$i++) {
	
	for(0..$#answer) {
		$answer[$_]*=$i;
	}
		
	for(0..$answer) {
		$answer[$_+1] += int($answer[$_]/10);
			$carry++; $array1[$a2]-=10;
		}
		if($carry!=0) {
			$array1[$a2+1]+=$carry;
		}
	}
}

for ($i=$#array1;$i>=0;$i--) {
	print "$array1[$i]";
}

print "\n";
[/php]

---

### Post by ConMan318 on 2008-05-24
I am pretty sure you will never be able to get C, without external libraries, to be able to calculate something like 100!.  I think it starts screwing up at around 15! or something like that, so for something like 100! I think you are out of luck with gcc.  C++ can handle larger numbers, but for something as big as 100!, I don't think even C++ would cut it.  You could write it in Python, which can handle it.

Keep in mind that a lot of the Project Euler problems are about finding a mathematical simplification or pattern that makes it unnecessary to actually calculate the giant numbers that it seems like you would need to calculate.  Obviously, I don't know if that is the case for the one you are doing, but just a reminder.

Which problem are you attempting, just out of curiosity?

EDIT: Looks like problem 20, which I don't think can be brute-forced in C.

---

### Post by slavik on 2008-05-24
python has a built in bignum, that is why it can handle very large numbers.

the code I wrote above will find 1000! in about 5 seconds (the C version is 0.5 seconds).

---

### Post by LaRoza on 2008-05-24
I wrote this in Fortran 77. You will need gfortran to compile it. (sudo aptitude install gfortran)



```

c File name: math.f
c
c
c FUNCTIONS RETURNS FACTORIAL
c MAX VALUE IS 170
        double precision function factorial(n)
            double precision n,i,g
            i = n 
            g = n
        if (n .eq. 0) then
            factorial = 1
            return 
        elseif (n .lt. 0) then
            factorial = -1
            return
        endif
   10   if (g .gt. 1) then
            i =  i * (g-1)
            g = g -1
            goto 10
        endif    
        factorial = i
    
        return
        end

```

Main program:
```

c File name factorial.f
c
c
c Start of program
        program fact
            double precision x,y
            write (*,*) 'Enter a number: '
            read (*,*) y
            x = factorial(y)
            write (*,*) 'Factorial of ', y , ' is, ', x
        stop
        end

```

Compile with:
```

gfortran -c math.f
gfortran -o test math.o factorial.f

```

Usage:
```

$./test
 Enter a number: 
170 
 Factorial of    170.000000000000       is,   7.257415615308004E+306
$

```

Calculates very quickly, no discernable time gap.

.002s for the calculation (changed the "read(*,*)" line to "y = 170" and timed it)

---

### Post by JupiterV2 on 2008-05-24
> Keep in mind that a lot of the Project Euler problems are about finding a mathematical simplification or pattern that makes it unnecessary to actually calculate the giant numbers that it seems like you would need to calculate. Obviously, I don't know if that is the case for the one you are doing, but just a reminder.


I usually struggle with  Project Euler because my mathematical skills aren't particularly strong. I have definitely found that there is an algorithm or clever method of finding the result without using brute force.

However, it seems that C would struggle with this problem as I wouldn't even be able to display the result with it. I'll try and tackle it another way.

---

### Post by LaRoza on 2008-05-24
> **JupiterV2 said:**
> I usually struggle with  Project Euler because my mathematical skills aren't particularly strong. I have definitely found that there is an algorithm or clever method of finding the result without using brute force.

However, it seems that C would struggle with this problem as I wouldn't even be able to display the result with it. I'll try and tackle it another way.

I did 170 with Fortran, do you need it to go higher than that?

---

### Post by Majorix on 2008-05-24
Python would handle it. You don't have to do anything :)

---

### Post by dwhitney67 on 2008-05-24
> **JupiterV2 said:**
> I usually struggle with  Project Euler because my mathematical skills aren't particularly strong. I have definitely found that there is an algorithm or clever method of finding the result without using brute force.

However, it seems that C would struggle with this problem as I wouldn't even be able to display the result with it. I'll try and tackle it another way.

You are worrying about Project Euler... heck, most people can't even do their taxes.

Really... think about it... are you trying to get a job at the (horse) race track trying to compute statistics, or do you want to do real software programming.

Try to come up with something that is practical.  I passed thru 4 years of Engineering school taking every math course known to man... only to realize that the only operations that are important are:  addition, subtraction, multiplication, and division.

Addition:  How much are you going to pay me?
Subtraction:  How much will that cost me?
Multiplication:  Three for a dollar?
Division:  Buy 3 (beers?) and get one free!

And life goes on.

---

### Post by CptPicard on 2008-05-24
> **dwhitney67 said:**
> 
Really... think about it... are you trying to get a job at the (horse) race track trying to compute statistics, or do you want to do real software programming.

Well, why, I actually do something like the former for a living ;)

Fortunately, my software doesn't need to be very engineered... as long as it is fast and produces the right numbers ;)

---

### Post by JupiterV2 on 2008-05-24
> **dwhitney67 said:**
> You are worrying about Project Euler... heck, most people can't even do their taxes.

Really... think about it... are you trying to get a job at the (horse) race track trying to compute statistics, or do you want to do real software programming.

Try to come up with something that is practical.  I passed thru 4 years of Engineering school taking every math course known to man... only to realize that the only operations that are important are:  addition, subtraction, multiplication, and division.

Addition:  How much are you going to pay me?
Subtraction:  How much will that cost me?
Multiplication:  Three for a dollar?
Division:  Buy 3 (beers?) and get one free!

And life goes on.

All I can say is...LOL! Awesome reply!

---

### Post by slavik on 2008-05-24
> **JupiterV2 said:**
> I usually struggle with  Project Euler because my mathematical skills aren't particularly strong. I have definitely found that there is an algorithm or clever method of finding the result without using brute force.

However, it seems that C would struggle with this problem as I wouldn't even be able to display the result with it. I'll try and tackle it another way.
look at my Perl code, you can pretty much copy/paste that (except that the array answer needs to be pre-allocated).

---

### Post by LaRoza on 2008-05-24
> **dwhitney67 said:**
>  only to realize that the only operations that are important are:  addition, subtraction, multiplication, and division.

Addition:  How much are you going to pay me?
Subtraction:  How much will that cost me?
Multiplication:  Three for a dollar?
Division:  Buy 3 (beers?) and get one free!


Actually, there are only two. Addition and Multiplication (subtraction and division are just those two operations.)

---

### Post by JupiterV2 on 2008-05-25
I got to thinking though, a Bignums library must implement some sort of link between two integers to express a large number with standard types.

If say...an int can only hold an unsigned value of 10 (0-9). In order to express a number like 100, you would need 3 int values stringed together (1, 0, 0). I also note that this is no different than writing a number by means of base 10:

ones = 10^0
tens = 10^1
huns = 10^2

Could I not then create a method of expressing a number base sizeof(int) to create a bignum style container in C?

```

// theoretical C bignum
struct bignum
{
  // [0] = ^1, [1] = ^2, [2] = ^3, ... , [n] = ^[n+1]
  int x[3]; // arbitrary number to contain the bignum
};

struct bignum bignum_add(int x, int y)
{
  // something clever to assign the variables...
}

int main()
{
  struct bignum bnum;

  bnum = bignum_add(7, 3);
}
```

Python was, if I'm not mistaken, written in C if not in totality than in part. If it can utilize bignums then C must in some way too. I think I'll sleep on this and think of how to come up with it without searching out any source to peek at.

I have a feeling that managing bits will be the key...shifting certain bits to be representative of certain numbers then stitching together everything to print the number...

The purpose, btw, of doing the problems on Project Euler is not to forsake "real" programming (which I also do) but exercise my mind and think outside of the box. A good programmer, by my estimation, finds unique methods of solving complex issues by maintaining simplicity and efficiency. Solving problems, even if unrelated to the task at hand, is akin to the reason why athletes stretch before they exercise. We need to limber up the mind!

---

### Post by dwhitney67 on 2008-05-25
Come on... a 32-bit unsigned integer can hold a value equal to (2^32)-1... or
4294967295.  Slightly larger than the value of 10.

Were not dealing with an abacus here, which even if we were, would be missing many beads if you were somehow correct in your assessment.

---

### Post by slavik on 2008-05-25
there are bignum libraries for C ... one of which is written by GNU.

---

### Post by achelis on 2008-05-25
> **dwhitney67 said:**
> Come on... a 32-bit unsigned integer can hold a value equal to (2^32)-1... or
4294967295.  Slightly larger than the value of 10.

Were not dealing with an abacus here, which even if we were, would be missing many beads if you were somehow correct in your assessment.

I believe he used 10 as an example for simplicity.

---

### Post by nvteighen on 2008-05-25
For Bignum, get the GNU Multi-Precision Library (GMP). It's on the repos (libgmp3-dev) and very nice to use... Don't forget to download the docs from [http://gmplib.org/](http://gmplib.org/) or you'll be clueless.

---

### Post by Lster on 2008-05-25
100! isn't that big. It's only 158 digits long in base 10:

```
93326215443944152681699238856266700490715968264381621468592963895217599993229915608941463976156518286253697920827223758251185210916864000000000000000000000000
```

[QUOTE=LaRoza]Actually, there are only two. Addition and Multiplication (subtraction and division are just those two operations.)[/QUOTE]

How can you work out 100 / 25 like that?

However if you consider just using subtraction and division, you can then do addition and multiplication relatively easily. For example:

x+y = x-(0-y)
x*y = x/(1/y)

I don't see how you can do the same with addition and multiplication but in inverse.

---

### Post by nvteighen on 2008-05-25
> **Lster said:**
> 
How can you work out 100 / 25 like that?

However if you consider just using subtraction and division, you can then do addition and multiplication relatively easily. For example:

x+y = x-(0-y)
x*y = x/(1/y)

I don't see how you can do the same with addition and multiplication but in inverse.

You can do it using [equivalence classes]("http://en.wikipedia.org/wiki/Equivalence_class"). Basically, division is defined for two coordinate pairs (a,b) and (c,d) iff a*d = b*c... (a,b) is afterwards used to define rational numbers (IR), which are usually written as a/b.

Substraction is the same, but iff a+d = b+c and the coordinate pair defines integer numbers instead (IZ).

EDIT: Now you see why division by zero is undefined ;)

---

### Post by Lster on 2008-05-25
Could you give an example? Maybe the one I gave (100 / 25)... I don't really understand.

---

### Post by nvteighen on 2008-05-25
You define an equivalence class for a number x (notated [x]) by a set of numbers that hold a given relationship between them.

So, let's define [x] = {(a,b) in IN, (c,d) in IN / ad = bc} (IN = set of natural numbers; / means here "so that")

So, we can say [100] = {(200, 2), (400, 4) / 200*4 = 400*2}, but this is also true for (1000, 10) and (500, 5) 1000*5 = 10*500, and infinite pairs of coordinate points.

[x] is a set which is generated by that relationship, which we can convieniently call "division" (200/2 = 400/4 = 1000/10 = etc = 100) ;) 

Actually, what we're doing here is to define what are rational numbers and a similar thing is done to create complex numbers or whatever you need.

(This comes from a lecture I had some years ago. The teacher came in saying: "Hello! Today we'll re-invent substraction and division")

---

### Post by Lster on 2008-05-25
Right. But algorithmically would that not involve trial and error (IE: trying all the different pairs...)? Also that operation could take an infinite amount of time unless you did it in a "smart" way. And doing it the smart way would require comparison and other operations. So effectively you can't really use *just* multiplication to do division... :)

---

### Post by nvteighen on 2008-05-25
> **Lster said:**
> Right. But algorithmically would that not involve trial and error (IE: trying all the different pairs...)? Also that operation could take an infinite amount of time unless you did it in a "smart" way. And doing it the smart way would require comparison and other operations. So effectively you can't really use *just* multiplication to do division... :)
Nope. This is a mathematical definition (I supposed you were asking for this!), not an algorithm and I don't think there are libraries that support this kind of logical analysis... are there?

If there was a way to shortcut division just with multiplication, programmer's life would be really easier! (sighs)

---

### Post by Lster on 2008-05-25
I think we may be discussing different aspects. I get your point though. :)

---

### Post by WW on 2008-05-25
> **LaRoza said:**
> I wrote this in Fortran 77. You will need gfortran to compile it. [...]


Just a quick note: except for very small integers, LaRoza's Fortran code to compute the factorial will not give the exact value.  Since the Project Euler problems tend to look for exact answers, that code might not be suitable.

The problem is that a floating point representation of a number (in this case, Fortran's double precision) has a finite number of digits of precision, and it doesn't take a very large integer to exceed this limit when computing the factorial.  For example, this Python script shows that a floating point calculation of n! is not exact when n=23:

**factorial_comparison.py**
```

m = 1
f = 1.0
n = 1
while (m == f):
    n += 1
    m *= n
    f *= n
    print "n=%d n!=%d  f=%-24.1f" % (n,m,f)
print "Floating point value of %d! is not exact." % n

```
Run:
```

$ python factorial_comparsion.py 
n=2 n!=2  f=2.0                     
n=3 n!=6  f=6.0                     
n=4 n!=24  f=24.0                    
n=5 n!=120  f=120.0                   
n=6 n!=720  f=720.0                   
n=7 n!=5040  f=5040.0                  
n=8 n!=40320  f=40320.0                 
n=9 n!=362880  f=362880.0                
n=10 n!=3628800  f=3628800.0               
n=11 n!=39916800  f=39916800.0              
n=12 n!=479001600  f=479001600.0             
n=13 n!=6227020800  f=6227020800.0            
n=14 n!=87178291200  f=87178291200.0           
n=15 n!=1307674368000  f=1307674368000.0         
n=16 n!=20922789888000  f=20922789888000.0        
n=17 n!=355687428096000  f=355687428096000.0       
n=18 n!=6402373705728000  f=6402373705728000.0      
n=19 n!=121645100408832000  f=121645100408832000.0    
n=20 n!=2432902008176640000  f=2432902008176640000.0   
n=21 n!=51090942171709440000  f=51090942171709440000.0  
n=22 n!=1124000727777607680000  f=1124000727777607680000.0
n=23 n!=25852016738884976640000  f=25852016738884978212864.0
Floating point value of 23! is not exact.
$ 

```

---

### Post by LaRoza on 2008-05-31
For those that didn't like my Fortran example and made fun of me (I know, I am being dramatic ;))

Haskell:
```

~$cat p.hs
factorial :: Integer -> Integer
factorial n = 
    if n == 1
        then 1
        else n * factorial (n-1)

main = do
    putStrLn "Enter number: "
    number <- getLine
    
    putStrLn (show (factorial (read number)))



~$./fact
Enter number: 
170
7257415615307998967396728211129263114716991681296451376543577798900561843401706157852350749242617459511490991237838520776666022565442753025328900773207510902400430280058295603966612599658257104398558294257568966313439612262571094946806711205568880457193340212661452800000000000000000000000000000000000000000

```

---

### Post by LaRoza on 2008-06-01
That Haskell examples works with numbers up very high. The highest I ran it with without a stack overflow was 500000, but I didn't wait for it to finish (1000000 gets a stack overflow in less time than I waited). I did get 100000 in a reasonable amount of time, but it was too big to open with a text editor and even cat was slow to output it. You'll have to run it yourself if you are interested in what 100000! is.

---

### Post by Bichromat on 2008-06-01
I've been reading up on Haskell since this morning (it's 17:00 here), and I found the simpler code below to be much faster:
```

factorial n = product [1..n]

main = do
    putStrLn "Enter number: "
    number <- getLine

    print (factorial (read number))

```

Haskell is very nice. To do the same thing in C, you need GMP, and the resulting code isn't much faster...

---

