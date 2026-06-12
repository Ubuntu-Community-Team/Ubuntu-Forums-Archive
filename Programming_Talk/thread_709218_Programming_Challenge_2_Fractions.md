---
title: "Programming Challenge 2: Fractions"
date: 2008-02-27
forum: Programming Talk
---

### Post by Lster on 2008-02-27
So it seems I must pick the next challenge. :)

*Drum roll* This weeks challenge is... to implement a simple fractions library that can manipulate fractions in various ways. Probably, you will want to implement a class to store the fraction with a numerator and denominator. As usual, creativity, efficiency and elegance are weighed to decide the winner. *Any* language is welcome - and the elegance is subjective to that language.

The implementation must provide the following functions:

[LIST]
[*]It must have a function for making a new fraction, setting the numerator and denominator. For example, it could be called Fraction_Create.
[*]A function for multiplying two fractions, returning a new fraction as output. It could be called Fraction_Multiply.
[*]A function for printing the fraction, such as Fraction_Print. It can print the fraction as either a top heavy fraction or a mixed fraction.
[/LIST]

Bonus features (for more points):

[LIST]
[*]A function for returning the reciprocal of a fraction.
[*]Functions for addition, subtraction and division (of fractions).
[*]The ability to simplify fractions and only ever returning fully simplified fractions from any of the functions listed will get you bonus points.
[*]A function to convert a fraction to an approximate decimal.
[*]A function to convert a decimal to an approximate fraction. Clever algorithms here will get you bonus points!
[/LIST]

You can't use any fraction libraries already created - you must code them from scratch! A winner will be picked on Wednesday the fifth of March based on the above.

Good luck and if you have any question, post them here! :)
Lster

---

### Post by insineratehymn on 2008-02-27
Haha, I just had to write this program for my intro to C++ class...

Where do I submit it to?

---

### Post by LaRoza on 2008-02-27
Note, this was written as soon as I got up, and saw this thread. So it isn't the best, obviously, that I could do.

**Updating**
**main.c:**
[php]
#include <stdio.h>
#include <stdlib.h>
#include "fraction.h"

int main(int args,char*argv)
{
    Fraction x = newFraction(3,2);
    Fraction y = newFraction(5,7);
    Fraction z = getReciprocal(y);

    Fraction added = addFraction(x,y);
    Fraction subbed = subFraction(x,y);
    Fraction mult = multiplyFraction(x,y);
    Fraction div = divideFraction(x,y);


    printFraction(x,0);
    printFraction(y,0);
    printFraction(z,0);

    printFraction(x,1);
    printFraction(y,1);
    printFraction(z,1);

    printFraction(added,0);
    printFraction(subbed,0);
    printFraction(mult,0);
    printFraction(div,0);

    deleteFraction(x);
    deleteFraction(y);
    deleteFraction(z);
    deleteFraction(added);
    deleteFraction(subbed);
    deleteFraction(mult);
    deleteFraction(div);

    return 0;
}
[/php]

**Output:**
```

3/2
5/7
7/5
1 1/2
5/7
2 2/5
31/14
11/14
15/14
21/10


```

**fraction.h**
[php]
typedef struct
{
    int num;
    int denom;
} * Fraction;

Fraction addFraction(Fraction,Fraction);
Fraction divideFraction(Fraction,Fraction);
Fraction getReciprocal(Fraction);
Fraction multiplyFraction(Fraction,Fraction);
Fraction newFraction(int,int);
Fraction subFraction(Fraction,Fraction);

void deleteFraction(Fraction);
int getCommonDenom(Fraction,Fraction);
void printFraction(Fraction,int);
[/php]

**fraction.c**
[php]
#include <stdio.h>
#include <stdlib.h>
#include "fraction.h"
Fraction addFraction(Fraction f, Fraction f2)
{
    int commonDenom = getCommonDenom(f,f2);
    return newFraction(((commonDenom/f->denom) * f->num)+((commonDenom/f2->denom) * f2->num),commonDenom);
}

Fraction divideFraction(Fraction f, Fraction f2)
{
    Fraction temp = getReciprocal(f2);
    Fraction divideFraction = multiplyFraction(f,temp);
    deleteFraction(temp);
    return divideFraction;
}

Fraction subFraction(Fraction f, Fraction f2)
{
    int commonDenom = getCommonDenom(f,f2);
    return newFraction(((commonDenom/f->denom) * f->num)-((commonDenom/f2->denom) * f2->num),commonDenom);
}

Fraction getReciprocal(Fraction f)
{
    return newFraction(f->denom,f->num);
}

Fraction multiplyFraction(Fraction f,Fraction f2)
{
    return newFraction(f->num * f2->num,f->denom * f2->denom);
}

Fraction newFraction(int x,int y)
{
    Fraction f = malloc(sizeof(Fraction));
    f && y != 0 ? f->num = x, f->denom = y : printf("Error in init, denominator = %d numerator = %d",x,y);
    return f;
}


void deleteFraction(Fraction f)
{
    free(f);
}
int getCommonDenom(Fraction f, Fraction f2)
{
    return f->denom * f2->denom;
}
void printFraction(Fraction f,int mode)
{
    mode == 0 ? printf("%d/%d\n",f->num,f->denom) : f->denom == 1 ? printf("%d\n",f->num) : f->num > f->denom ? printf("%d %d/%d\n",f->num / f->denom,f->num - ((f->num / f->denom) * f->denom),f->denom) : printFraction(f,0);
}
[/php]

It is a mix of fulflilling the specs in the OP, rapid coding, and trying to confuse new C coders.

---

### Post by Lster on 2008-02-27
Very nice. How about add, subtract and canceling? :)

---

### Post by LaRoza on 2008-02-27
> **Lster said:**
> Very nice. How about add, subtract and canceling? :)

I haven't:

* eaten
* drank
* gotten fully dress
* read the paper
* looked for job (do it every day)

Finishing the library will have to wait. I have priorities (and coding this showed where some of them are)

(Note, anyone who doesn't see the point of pointers, read the code, and try to do it without pointers)

**Updated to include other operations, sorry, nothing fancy or clever going on**

---

### Post by Lster on 2008-02-27
[QUOTE=LaRoza]I haven't:

* eaten
* drank
* gotten fully dress
* read the paper
* looked for job (do it every day)

Finishing the library will have to wait. I have priorities (and coding this showed where some of them are)[/QUOTE]

I guess you're in a different time zone to me. :)

---

### Post by LaRoza on 2008-02-27
> **Lster said:**
> I guess you're in a different time zone to me. :)

I got up later than normal, it is midday now.

---

### Post by ruy_lopez on 2008-02-27
Another objc implementation (I'm learning objc, if you hadn't guessed).

```

#import <objc/Object.h>

// Define the Fraction class
@interface Fraction : Object
{
	int numerator;
	int denominator;
}
- (Fraction *) initWith: (int) n: (int) d;
- (void) setNumerator: (int) n;
- (void) setDenominator: (int) d;
- (void) setTo: (int) n over: (int) d;
- (int)	numerator;
- (int)	denominator;
- (void) reduce;
- (double) convertToNum;
- (void) print;
- (void) printMixed;
@end

// Define the MathOps category
@interface Fraction (MathOps)
- (Fraction *) add: (Fraction *) f;
- (Fraction *) mul: (Fraction *) f;
- (Fraction *) sub: (Fraction *) f;
- (Fraction *) div: (Fraction *) f;
- (Fraction *) reciprocal: (Fraction *) f;
@end

```

```

#import "Fraction.h"
#import <stdio.h>
#include <math.h>
#include <stdlib.h>

@implementation Fraction;
-(Fraction *) initWith: (int) n: (int) d;
{
	self = [ super init ];

	if (self)
		[ self setTo: n over: d ];

	return self;
}

-(void) setNumerator: (int) n
{
	numerator = n;
}

-(void) setDenominator: (int) d
{
	denominator = d;
}

-(int) numerator 
{
	return numerator;
}

-(int) denominator
{
	return denominator;
}

-(double) convertToNum
{
	if (denominator != 0)
		return (double) numerator / denominator;
	else
		return 0.0;
}

-(void) setTo: (int) n over: (int) d
{
	numerator = n;
	denominator = d;
}

- (void) reduce
{
	int	u = numerator;
	int	v = denominator;
	int	temp;

	if (u < 0)
		u = -u;

	while (v != 0) {
		temp = u % v;
		u = v;
		v = temp;
	}

	numerator /= u;
	denominator /= u;
}	

-(void) print 
{
	printf (" %i/%i ", numerator, denominator);
}

- (void) printMixed
{
	Fraction *result = [[Fraction alloc] init];
	int whole_part;
	div_t tdiv;

 	if (numerator >= denominator) {
		if (numerator == denominator) {
			printf(" 1 ");
			return;
		}
		tdiv = div(numerator, denominator);
		whole_part = tdiv.quot;
		if (tdiv.rem != 0) {
			[result setTo: tdiv.rem over: denominator];
			[result reduce];
			printf(" %i+%i/%i ", whole_part, [result numerator], 
                                                                  [result denominator]);
			return;
		}
		else {
			printf(" %i ", whole_part);
			return;
		}
	}
	else
		[self print];
}
@end

/* MathOps category implementation */
@implementation Fraction (MathOps);
-(Fraction *) add: (Fraction *) f
{
	Fraction *result = [[Fraction alloc] init];
	int resultNum, resultDenom;

	resultNum = (numerator * [f denominator]) + 
		(denominator * [f numerator]);
	resultDenom = denominator * [f denominator];
	[result setTo: resultNum over: resultDenom];
	[result reduce];

	return result;
}

-(Fraction *) sub: (Fraction *) f
{
	Fraction *result = [[Fraction alloc] init];
	int resultNum, resultDenom;

	resultNum = (numerator * [f denominator]) - 
		(denominator * [f numerator]);
	resultDenom = denominator * [f denominator];
	[result setTo: resultNum over: resultDenom];
	[result reduce];

	return result;
}

- (Fraction *) mul: (Fraction *) f
{
	Fraction *result = [[Fraction alloc] init];

	[result setTo: numerator * [f numerator]
		 over: denominator * [f denominator]];
	[result reduce];

	return result;
}

- (Fraction *) div: (Fraction *) f
{
	Fraction *result = [[Fraction alloc] init];

	[result setTo: numerator * [f denominator]
		 over: denominator * [f numerator]];
	[result reduce];

	return result;
}

- (Fraction *) reciprocal: (Fraction *) f
{
	Fraction *result = [[Fraction alloc] init];

	[result setTo: denominator over: numerator];
	[result reduce];

	return result;
}
@end

```

```

#import "Fraction.h"

int main (int argc, char *argv[])
{
	Fraction  *a;
	Fraction  *b;
	Fraction  *result;
	
	a = [[Fraction alloc] init];
	b = [[Fraction alloc] init];

	[a setTo: 4 over: 3];
	[b setTo: 2 over: 8];

	[a print]; 
	printf (" + "); 
	[b print]; 
	printf (" = ");
	result = [a add: b];
	[result print];
	printf("\t = ");
	[result printMixed];
	printf("\t = %e\n", [result convertToNum]);

	[a print];
	printf(" - ");
	[b print];
	printf(" = ");
	result = [a sub: b];
	[result print];
	printf("\t = ");
	[result printMixed];
	printf("\t = %e\n", [result convertToNum]);

	[a print]; 
	printf (" * "); 
	[b print]; 
	printf (" = ");
	result = [a mul: b];
	[result print];
	printf("\t\t\t = %e\n", [result convertToNum]);

	[a print]; 
	printf(" / "); 
	[b print]; 
	printf(" = ");
	result = [a div: b];
	[result print];
	printf("\t = ");
	[result printMixed];
	printf("\t = %e\n", [result convertToNum]);

	[a free];
	[b free];
	[result free];

	return 0;
}

```

compile with -lobjc and -lm

EDIT: added printMixed to handle mixed fractions. I might add convert decimal to fraction later. (I'm getting whitespace inserted into my code blocks when I post)

---

### Post by insineratehymn on 2008-02-27
Like I said above, I had to write this program for a class anyway...
The teacher is kind of weird, he won't let us use anything that he hasn't taught us yet... so no classes or anything.


Das Code:
```

#include <iostream>
#include <string>
using namespace std;

// End pre-processor directives...

/*
  Program: Team Project
  Author: CHRIS TERRY
  Date written: 2/20/2008
  
  This of each fractal equation like this:
  (numeratorOne / denominatorOne) + (numeratorTwo / denominatorTwo)

  This is of course assuming that you want to add them.
  Assumptions/Checks: 
    Denominators are NOT 0
    Menu choices can only be 0 - 5
    The user only wants to do an equation regarding two(2) fractions
    There are NO command args
    Debug mode is choice 5 on the menu, it will restart the menu

  If you got this, please use it appropriately.
*/
    

bool DEBUG = false;

// Global debug variable...

void menu(int&);
void addFractions(int, int, int, int, int&, int&);
void subtractFractions(int, int, int, int, int&, int&);
void multiplyFractions(int, int, int, int, int&, int&);
void divideFractions(int, int, int, int, int&, int&);
void getNumbers(int&, int&, int&, int&, char);
int returnProduct(int, int);

// End method prototyping...

int main() {
  
  int finalNumerator, finalDenominator;
  // The finals...
  
  int numeratorOne, numeratorTwo, denominatorOne, denominatorTwo;
  // The numbers the will enter...

  int menuChoice = 0;
  // The menu item they enter...

  char symbol;
  // Which symbol for the equation...

  menu(menuChoice);
  // Get which method they want to do...

  switch(menuChoice) {
    // Determines which symbol based on which operation they want to perform...

  case 1: symbol = '+'; break;
  case 2: symbol = '-'; break;
  case 3: symbol = 'x'; break;
  case 4: symbol = '/'; break;
  }
  // End switch-case...

  getNumbers(numeratorOne, numeratorTwo, denominatorOne, denominatorTwo, symbol);
  // Get their numbers...

  if(DEBUG) cout << endl <<  numeratorOne << denominatorOne << numeratorTwo << denominatorTwo << endl;
  // Debug code...

  switch(menuChoice) {
    // Switch to determine witch method to call...

  case 1: {
    // The addition case...

    addFractions( numeratorOne, numeratorTwo, denominatorOne, denominatorTwo, finalNumerator, finalDenominator);
    // Call the method...

     break;
  } 
  case 2: {
    // The subtraction case...
    
    subtractFractions ( numeratorOne, numeratorTwo, denominatorOne, denominatorTwo, finalNumerator, finalDenominator );
    // Call the method...

    break;
  }
  case 3: {
    // The multiplication case...
    
    multiplyFractions ( numeratorOne, numeratorTwo, denominatorOne, denominatorTwo, finalNumerator, finalDenominator );
    // Call the method...

    break;
  }
  case 4: {
    // The division case...

    divideFractions ( numeratorOne, numeratorTwo, denominatorOne, denominatorTwo, finalNumerator, finalDenominator );
    //Call the method...

    break;
  }
   
  }
  // End switch-case...

  cout << endl << "Your problem was: ( " << numeratorOne << " / " << denominatorOne
       << " ) " << symbol << " ( " << numeratorTwo << " / " << denominatorTwo << " )" << endl;
  // Output their original problem...
  
  cout << "Your answer is: " << finalNumerator << " / " << finalDenominator << endl;
  // Output the answer...

  cout << "Just for fun, the decimal answer is: " << (finalNumerator + 0.0) / (finalDenominator + 0.0) << endl;
  // I like to make sure the numbers are real, so output the decimal value...

  cout << "Remember, this program does NOT calculate the lowest common denominator." << endl;
  // Disclaimer...

  return 0;
  // Terminate the program...
}

void divideFractions( int numeratorOne, int numeratorTwo, int denominatorOne,
		      int denominatorTwo, int& finalNumerator, int& finalDenominator ) {
  // The division method...

  if(DEBUG) cout << endl << "divideFractions: Entering method..." << endl;
  // Debug code...

  int newNumerator = returnProduct(numeratorOne, denominatorTwo);
  // Get the numerator: numeratorOne * denominatorTwo

  int newDenominator = returnProduct(denominatorOne, numeratorTwo);
  // Get the denominator: denominatorOne * numeratorTwo

  finalNumerator = newNumerator;
  finalDenominator = newDenominator;
  // Set the references one we have both the values...

  if(DEBUG) cout << endl << finalNumerator << finalDenominator << endl;
  //Debug code...
}

void multiplyFractions( int numeratorOne, int numeratorTwo, int denominatorOne,
			int denominatorTwo, int& finalNumerator, int& finalDenominator ) {
  // The multiplication method...

  if(DEBUG) cout << endl << "multiplyFractions: Entering method..." << endl;
  // Debug code...

  int newNumerator = returnProduct(numeratorOne, numeratorTwo);
  // Get the numerator: numeratorOne * numeratorTwo

  int newDenominator = returnProduct(denominatorOne, denominatorTwo);
  // Get the denominator: denominatorOne * denominatorTwo
  
  finalNumerator = newNumerator;
  finalDenominator = newDenominator;
  // Apply the references once we have the values...

  if(DEBUG) cout << endl << finalNumerator << finalDenominator << endl;
  // Debug code...
}

int returnProduct( int numberOne, int numberTwo ) {
  return numberOne * numberTwo;
  // All this method does is return the product of variable 1 by variable 2...
}

void subtractFractions ( int numeratorOne, int numeratorTwo, int denominatorOne, 
			 int denominatorTwo, int& finalNumerator, int& finalDenominator ) {
  // The subtraction method...

  if(DEBUG) cout << endl << "subtractFractions: Entering method... " << endl;
  // Debug code...

  int commonDenominator = returnProduct( denominatorOne, denominatorTwo );
  // Get the common denominator: denominatorOne * denominatorTwo

  int newNumeratorOne = returnProduct(numeratorOne, denominatorTwo);
  // Get the first numerator: numeratorOne * denominatorTwo

  int newNumeratorTwo = returnProduct(numeratorTwo, denominatorOne);
  // Get the second numerator: numeratorTwo * denominatorOne

  finalNumerator = newNumeratorOne - newNumeratorTwo;
  // The final numerator is the first minus the second...

  finalDenominator = commonDenominator;
  // Apply the references one we compute the values...

  if(DEBUG) cout << endl << commonDenominator << finalNumerator << finalDenominator << endl;
  // Debug code...
}

void addFractions ( int numeratorOne, int numeratorTwo, int denominatorOne, 
		    int denominatorTwo, int& finalNumerator, int& finalDenominator) {
  if(DEBUG) cout << endl << "addFractions: Entering method..." << endl;
  // Debug code...
  
  int commonDenominator = returnProduct(denominatorOne , denominatorTwo);
  // Calculate the common denominator...

  int newNumeratorOne = returnProduct(numeratorOne , denominatorTwo);
  // Calculate the first new numerator...

  int newNumeratorTwo = returnProduct(numeratorTwo , denominatorOne);
  // Calculate the second new numerator...

  finalNumerator = newNumeratorOne + newNumeratorTwo;
  // Calculate the final numerator...

  finalDenominator = commonDenominator;
  // Calculate the final denominator...

  if(DEBUG) cout << endl << commonDenominator << finalNumerator << finalDenominator << endl;
  // Debug code...
}

void getNumbers( int& numeratorOne, int& numeratorTwo, int& denominatorOne, int& denominatorTwo, char symbol) {
  // This method just gets the numbers from the user with a pretty menu...

  if(DEBUG) cout << endl << "getNumbers: Entering method..." << endl;
  // Debug code...

  do {
    cout << endl << "I am here to get your desired numerators and denominators" << endl;
    cout << "Please enter them in this fashion: 1 2 3 4" << endl;
    cout << "Please note the SPACES between the numbers." << endl;
    cout << "Thus, 1 2 3 4 would mean: ( 1 / 2 ) " << symbol << " ( 3 / 4 ) " << endl;
    cout << "I'll take those numbers now: ";
    // Output a nice little input prompt...

    cin >> numeratorOne >> denominatorOne >> numeratorTwo >> denominatorTwo;
    // Get the numbers...

    if((denominatorOne == 0) || (denominatorTwo == 0)) {
      cout << endl << "You cannot have a denominator equal to 0. Please try again." << endl;
    }
    // Check for division by 0...

  } while ( (denominatorOne == 0) || (denominatorTwo == 0));
    // Run while the denominators are equal to 0...
   
}

void menu(int& menuChoice) {
  // This is the menu method, it passes the choice back up to main...
  
  do {
    cout << "Welcome to the fraction calculator" << endl;
    cout << "Your choices are:" << endl;
    cout << "\t0) Replay Menu" << endl;
    cout << "\t1) Add Fractions" << endl;
    cout << "\t2) Subtract Fractions" << endl;
    cout << "\t3) Multiply Fractions" << endl;
    cout << "\t4) Divide Fractions" << endl;
    ( DEBUG ) ? cout << "\t5) DEBUG MODE OFF" << endl : cout << "\t5) DEBUG MODE ON" << endl;
    cout << "Please enter your choice( ex. 1 ): ";
    cin >> menuChoice;
    // Get the actual choice after advisal...
    if ( menuChoice == 5 ) {
      DEBUG = !DEBUG;
      menuChoice = 0;
    }
    if ( ( menuChoice < 0 ) || ( menuChoice > 5 ) ) {
      cout << "Please enter a number 0 - 4." << endl;
      menuChoice = 0;
    }
    // If it is 0 (or anything else), we will reprint the menu...

  } while( menuChoice == 0 );
  // End menu...

  if(DEBUG) cout << endl << "Menu: Exit do-while... " << menuChoice << endl;
  // Debug code...
}


```
Output:
```

Welcome to the fraction calculator
Your choices are:
        0) Replay Menu
        1) Add Fractions
        2) Subtract Fractions
        3) Multiply Fractions
        4) Divide Fractions
        5) DEBUG MODE ON
Please enter your choice( ex. 1 ): 5
Welcome to the fraction calculator
Your choices are:
        0) Replay Menu
        1) Add Fractions
        2) Subtract Fractions
        3) Multiply Fractions
        4) Divide Fractions
        5) DEBUG MODE OFF
Please enter your choice( ex. 1 ): 1

Menu: Exit do-while... 1

getNumbers: Entering method...

I am here to get your desired numerators and denominators
Please enter them in this fashion: 1 2 3 4
Please note the SPACES between the numbers.
Thus, 1 2 3 4 would mean: ( 1 / 2 ) + ( 3 / 4 ) 
I'll take those numbers now: 1 2 3 4

1234

addFractions: Entering method...

8108

Your problem was: ( 1 / 2 ) + ( 3 / 4 )
Your answer is: 10 / 8
Just for fun, the decimal answer is: 1.25
Remember, this program does NOT calculate the lowest common denominator.


```

---

### Post by pedro_orange on 2008-02-27
> **LaRoza said:**
> 
**fraction.h**
[php]
typedef struct
{
    int num;
    int denom;
} * Fraction;

Fraction addFraction(Fraction,Fraction);
Fraction getReciprocal(Fraction);
Fraction multiplyFraction(Fraction,Fraction);
Fraction newFraction(int,int);
Fraction subFraction(Fraction,Fraction);

void deleteFraction(Fraction);
int getCommonDenom(Fraction,Fraction);
void printFraction(Fraction,int);
[/php] 

Very nice.
Forgot to declare:

Fraction divideFraction(Fraction,Fraction);

In the header. But otherwise, smashing stuff.

---

### Post by LaRoza on 2008-02-27
> **pedro_orange said:**
> Very nice.
Forgot to declare:

Fraction divideFraction(Fraction,Fraction);

In the header. But otherwise, smashing stuff.

I forgot to update the OP, it is in my code. Thanks for catching that, it means you probably read most of the code.

Thanks, it was somewhat fun to make. I didn't sit down and design it, just started coding.

Actually, I started with Python, but stopped after "class Fraction:" as it would have been boring to write. Pointers ftw.

---

### Post by Martin Witte on 2008-02-27
In one of the books on Python (How to think like a computer scientist) an outline for this exercise is given, see [http://openbookproject.net//thinkCSpy/app_c.xhtml](http://openbookproject.net//thinkCSpy/app_c.xhtml), but nevertheless here's mine in Python, not everything asked for is yet there, maybe if I find more time later....

[PHP]class FractionError(Exception):
    pass

class Fraction(object):
    """Class implements fractions
    supported operations:
    - Creation of a new fraction, e.g. f = Fraction(1, 2)
    - printing of a fraction, e.g. print f ('1/2')
    - comparing of fractions with other fractions and with integers, e.g.
      Fraction(6, 4) == Fraction(3, 2), Fraction(3, 2) != Fraction(1, 2),
      Fraction(9, 3) == 3, 3 == Fraction(3, 1)
    - Multiplication of fractions with other fractions and with integers, e.g.
      Fraction(1, 2) * Fraction(1, 2) == Fraction(1, 4),
      Fraction(1, 8) * 2 == fraction(1, 4)
    - Create a reciproke, e.g. 'print Fraction(3, 4).reciproke()'
      will print '4/3'
    - convert a fraction to a float, by a calling float(Fraction(3, 4))
    """
    def __init__(self, numerator, denominator):
        if denominator == 0:
            raise ZeroDivisionError
        if not isinstance(numerator, int) or isinstance(numerator, long):
            raise FractionError('numerator %s has not the right type'% \
                                str(numerator))
        if not isinstance(denominator, int) or isinstance(denominator, long):
            raise FractionError('denominator %s has not the right type'% \
                                str(denominator))
        
        self.numerator = numerator
        self.denominator = denominator

        def greatest_common_divisor(m, n):
            """Euclid algorithm"""
            if m % n == 0:
                return n
            else:
                return greatest_common_divisor(n, m % n)

        gcd = greatest_common_divisor(numerator, denominator)
        self.simplified_numerator = numerator / gcd
        self.simplified_denominator = denominator / gcd
        
    def __mul__(self, other):
        if isinstance(other, Fraction):
            product = Fraction(self.numerator*other.numerator, \
                               self.denominator*other.denominator)
            return Fraction(product.simplified_numerator, \
                            product.simplified_denominator)
        elif isinstance(other, int) or isinstance(other, long):
            product = Fraction(self.numerator*other, self.denominator)
            return Fraction(product.simplified_numerator, \
                            product.simplified_denominator)            
        else:
            raise FractionError('can not multiply %s with Fraction %s' %\
                                 (other, self))
    __rmul__ = __mul__

    def __float__(self):
        return (1.0 * self.numerator) / self.denominator
        
    def __str__(self):
        return "%d/%d" % (self.numerator, self.denominator)

    def __eq__(self, other):            
        if isinstance(other, Fraction):
            if self.simplified_numerator == other.simplified_numerator and \
               self.simplified_denominator == other.simplified_denominator:
                return True
            else:
                return False
        elif isinstance(other, int) or isinstance(other, long):
            if self.numerator / self.denominator == other and \
               self.numerator % self.denominator == 0:
                return True
            else:
                return False
        else:
            raise FractionError('can not compare %s with Fraction %s' %\
                                 (other, self))

    def reciproke(self):
        return Fraction(self.simplified_denominator, self.simplified_numerator)
                   
if __name__ == '__main__':
    import unittest
    class FractionTestCase(unittest.TestCase):
        def testInit(self):
            self.assertRaises(ZeroDivisionError, Fraction, 1, 0)
            self.assertRaises(FractionError, Fraction, 1.2, 8)
            self.assertRaises(FractionError, Fraction, 8, 1.2)

        def testPrint(self):
            self.assertEqual(str(Fraction(1,2)), '1/2')
        
        def testEquality(self):
            self.assertEqual(Fraction(3,2), Fraction(3,2))
            self.assertEqual(Fraction(3,2), Fraction(6,4))
            self.assertEqual(Fraction(4,2), 2)
            self.assertEqual(2, Fraction(4,2))
            self.assertNotEqual(1, Fraction(4, 3))
            self.assertNotEqual(Fraction(5, 4), Fraction(4, 3))
            self.assertRaises(FractionError, cmp, Fraction(1, 2), 1.2)
            self.assertRaises(FractionError, cmp, -0.2, Fraction(1, 2))

        def testMultiply(self):
            self.assertEqual(Fraction(3, 2) * Fraction(3, 2), Fraction(9, 4))
            self.assertEqual(Fraction(1,3) * 2, Fraction(2, 3))
            self.assertEqual(Fraction(1,8) * 2, Fraction(1, 4))
            self.assertEqual(2 * Fraction(1,3), Fraction(2, 3))

        def testReciproke(self):
            self.assertEqual(Fraction(7,3), Fraction(3,7).reciproke())
            self.assertNotEqual(Fraction(7,3), Fraction(3,8).reciproke())
            self.assertEqual(Fraction(7,3), Fraction(6,14).reciproke())

        def testFloat(self):
            self.assertEqual(float(Fraction(3, 4)), 0.75)
            self.assertEqual(float(Fraction(5, 4)), 1.25)
            self.assertNotEqual(float(Fraction(5, 4)), 1.250001)
            
    suite = unittest.TestLoader().loadTestsFromTestCase(FractionTestCase)
    unittest.TextTestRunner(verbosity=2).run(suite)
[/PHP]

---

### Post by aks44 on 2008-02-27
@LaRoza: looks like your mixed-mode output has some problems, eg. try to print 8/3 (or 14/3) with (mode = 1).

---

### Post by LaRoza on 2008-02-27
> **aks44 said:**
> @LaRoza: looks like your mixed-mode output has some problems, eg. try to print 8/3 (or 14/3) with (mode = 1).

Yes, I know.

**Fixed: it was so elementary too, I am ashamed.**

---

### Post by Wybiral on 2008-02-27
I don't actually want to win this one since I did the last one, but I still want to participate :)

Mine is in Python. It can take a number of forms in as the argument and construct the reduced fraction. My float-to-fraction conversion is a bit of a hack though (I convert the real number to a string, split it at the decimal point, then use 10 ^ length(decimal) as the denominator which *should* work most of the time). You can also create fractions from strings in the form of "numerator / denominator" and you can compare fractions. All of the operators can handle (fraction x (fraction, int, float, tuple, list, or string) form (but I didn't go out of my way to make them handle the right-sided form).

```

def gcd(a, b):
    """ Return greatest common denominator """
    mod = a % b
    return b if not(mod) else gcd(b, mod)

class Fraction:

    def __init__(self, *args):
        """ Arguments can be:
                integer numerator
                floating point decimal
                numerator, denominator
                (numerator, denominator)
                [numerator, denominator]
                "numerator / denominator"
        """
        if len(args) == 2:
            self.numerator, self.denominator = args
        else:
            arg = args[0]
            if isinstance(arg, tuple) or isinstance(arg, list):
                self.numerator, self.denominator = arg
            elif isinstance(arg, int) or isinstance(arg, long):
                self.numerator, self.denominator = arg, 1
            elif isinstance(arg, float):
                string = "%f" % arg
                self.denominator = 10 ** len(string.split(".")[1])
                self.numerator = int(arg * self.denominator)
            elif isinstance(arg, str):
                arg = arg.replace(' ', '').split("/")
                self.numerator, self.denominator = [int(x) for x in arg]
        gd = gcd(self.numerator, self.denominator)
        self.numerator = self.numerator / gd
        self.denominator = self.denominator / gd

    def ensure_type(self, b):
        """ Ensure that b is a fraction """
        return b if isinstance(b, Fraction) else Fraction(b)

    def reciprocal(self):
        return Fraction((self.denominator, self.numerator))

    def __mul__(self, b):
        b = self.ensure_type(b)
        n, d = self.numerator * b.numerator, self.denominator * b.denominator
        return Fraction((n, d))

    def __div__(self, b):
        return self * self.ensure_type(b).reciprocal()

    def __add__(self, b):
        b = self.ensure_type(b)
        n = self.numerator * b.denominator + self.denominator * b.numerator
        d = self.denominator * b.denominator
        return Fraction((n, d))

    def __sub__(self, b):
        b = self.ensure_type(b)
        n = self.numerator * b.denominator - self.denominator * b.numerator
        d = self.denominator * b.denominator
        return Fraction((n, d))

    def __cmp__(self, b):
        return cmp(float(self), float(self.ensure_type(b)))

    def __str__(self):
        return "%d/%d" % (self.numerator, self.denominator)

    def __float__(self):
        return float(self.numerator) / self.denominator

    def __int__(self):
        return self.numerator / self.denominator

if __name__ == "__main__":
    a = Fraction(0.5)
    b = Fraction("1 / 3")

    # Fraction to fraction operators
    print "%s + %s = %s" % (str(a), str(b), str(a + b))
    print "%s + %s = %s" % (str(a), str(b), str(a - b))
    print "%s * %s = %s" % (str(a), str(b), str(a * b))
    print "%s / %s = %s" % (str(a), str(b), str(a / b))

    # Fraction to int operators
    print "%s + 2 = %s" % (str(a), str(a + 2))
    print "%s - 2 = %s" % (str(a), str(a - 2))
    print "%s * 2 = %s" % (str(a), str(a * 2))
    print "%s / 2 = %s" % (str(a), str(a / 2))

    # Fraction to fraction comparisons
    print "%s < %s = %s" % (str(a), str(b), str(a < b))
    print "%s > %s = %s" % (str(a), str(b), str(a > b))
    print "%s == %s = %s" % (str(a), str(b), str(a == b))

```

EDIT:

Hmm... My float-to-fraction fails for numbers that get converted to scientific notation. I'll have to find some work around.

EDIT2:

OK, now it doesn't fail for scientific numbers (by enforcing a decimal string), but it does still have a pretty limited precision.

---

### Post by Siph0n on 2008-02-27
Since everyone else is doing C++/C/Python... thought I would switch it up :) Here it is in Ada95
```

-- Need to add the following...
-- Convert fraction to decimal

-- Convert decimal to fraction

-- Error checking



with Ada.Text_IO, Ada.Integer_Text_IO;

use Ada.Text_IO, Ada.Integer_Text_IO;



procedure fractions is

    -- New Type - Fraction

    type Fraction is

        record

            Num: Integer;

            Den: Integer;

        end record;

    -- 5 Fractions

    frac1 : Fraction := (5,9);

    frac2 : Fraction := (2,7);

    frac3 : Fraction := (2,4);

    frac4 : Fraction := (10,20);

    frac5 : Fraction := (34,17);



    -- Multiply 2 Fractions

    procedure MultFrac(Fract1,Fract2 : in Fraction) is

    begin

        Put(Fract1.Num*Fract2.Num,1);

        Put("/");

        Put(Fract1.Den*Fract2.Den,1);

        New_Line;

    end MultFrac;



    -- GCD

    function GCD(Num1, Num2: in Integer) return Integer is

    begin
        if Num2 = 0 then

            return Num1;

        else

            return GCD(Num2, Num1 mod Num2);

        end if;

    end GCD;



    -- Simplify

    procedure Simplify(Fract : in Fraction) is

    result : Integer;

    begin

        result := GCD(Fract.Num, Fract.Den);

        Put(Fract.Num/result,1);
	if Fract.Den/result = 1 then
            New_Line;

        else
       	    Put("/");

            Put(Fract.Den/result,1);
            New_Line;

        end if;

    end Simplify;

        

    -- Divide 2 Fractions

    procedure DivFrac(Fract1,Fract2 : in Fraction) is

    begin

        Put(Fract1.Num*Fract2.Den,1);

        Put("/");

        Put(Fract1.Den*Fract2.Num,1);

        New_Line;

    end DivFrac;



    -- Add 2 Fractions

    procedure AddFrac(Fract1,Fract2 : in Fraction) is

    begin

        Put((Fract1.Num*Fract2.Den)+(Fract2.Num*Fract1.Den),1);

        Put("/");

        Put(Fract1.Den*Fract2.Den,1);

        New_Line;

    end AddFrac;



    -- Subtract 2 Fractions

    procedure SubFrac(Fract1,Fract2 : in Fraction) is

    begin

        Put((Fract1.Num*Fract2.Den)-(Fract2.Num*Fract1.Den),1);

        Put("/");

        Put(Fract1.Den*Fract2.Den,1);

        New_Line;

    end SubFrac;



    -- Print Fraction

    procedure PrintFrac(Fract : in Fraction) is

    begin

        Put(Fract.Num,1);

        Put("/");

        Put(Fract.Den,1);

        New_Line;

    end PrintFrac;


    -- Switch Numerator and Denominator

    procedure RecipFrac(Fract : in Fraction) is

    begin

        Put(Fract.Den,1);

        Put("/");

        Put(Fract.Num,1);

        New_Line;

    end RecipFrac;



begin
    Put("Print Fractions");
    New_Line;

    PrintFrac(frac1); -- 5/9

    PrintFrac(frac2); -- 2/7

    PrintFrac(frac3); -- 2/4

    PrintFrac(frac4); -- 10/20

    PrintFrac(frac5); -- 34/17



    Put("Multiply Fraction");
    New_Line;

    MultFrac(frac1,frac2); -- 10/63

    MultFrac(frac2,frac3); -- 4/28

    MultFrac(frac1,frac3); -- 10/36



    Put("Divide Fractions");
    New_Line;

    DivFrac(frac1,frac2);

    DivFrac(frac2,frac3);

    DivFrac(frac1,frac3);



    Put("Add Fractions");
    New_Line;

    AddFrac(frac1,frac2);

    AddFrac(frac2,frac3);

    AddFrac(frac1,frac3);



    Put("Subtract Fractions");
    New_Line;

    SubFrac(frac1,frac2);

    SubFrac(frac2,frac3);

    SubFrac(frac1,frac3);


    Put("Recipricol Fractions");
    New_Line;

    RecipFrac(frac1); -- 9/5

    RecipFrac(frac2); -- 7/2

    RecipFrac(frac3); -- 4/2



    Put("Simplify Fractions");
    New_Line;

    Simplify(frac4); -- 1/2

    Simplify(frac5); -- 2

    Simplify(frac1); -- 5/9



end fractions;

```

---

### Post by slavik on 2008-02-27
> **LaRoza said:**
> 
```

Fraction newFraction(int x,int y)
{
    Fraction f = malloc(sizeof(Fraction));
    f && y != 0 ? f->num = x, f->denom = y : printf("Error in init, denominator = %d numerator = %d",x,y);
    return f;
}
```


are you sure that malloc call is proper?

```

typedef struct _blah {
	int a; double b; char c[100];
} * blah;

int main(int argc, char** argv)
{
	printf("%ld\n",sizeof(blah));
	return 0;
}
```

The above code outputs '8' (I am on a 64bit system).

---

### Post by themusicwave on 2008-02-27
Congratulations on your win in the last challenge!

This sounds like an interesting challenge with lots of extra credit.

I will be tackling this one at some point.  I will most likely do it in Python since I am still learning Python.  However, if there are too many Python submissions I could always do it in Java.  We shall see...

---

### Post by LaRoza on 2008-02-27
> **slavik said:**
> are you sure that malloc call is proper?

The above code outputs '8' (I am on a 64bit system).

What is wrong with the malloc? I don't see a problem with it, but then again, I am not an experienced programmer.

---

### Post by Wybiral on 2008-02-27
> **slavik said:**
> are you sure that malloc call is proper?

The above code outputs '8' (I am on a 64bit system).

It's true.

> **LaRoza said:**
> What is wrong with the malloc? I don't see a problem with it, but then again, I am not an experienced programmer.

It's not "malloc" that has a problem, it's "sizeof".

EDIT:

I removed my explanation since this is a challenge :)

---

### Post by KaeseEs on 2008-02-27
> **Wybiral said:**
> It's true.



It's not "malloc" that has a problem, it's "sizeof".

EDIT:

I removed my explanation since this is a challenge :)

I think this will explain it...
```
#include <stdio.h>

typedef struct _foo{
	int a;
	float b;
	char c[100];
} *foo;

int main(void){
	foo bar;
	printf("sizeof(foo) == %d\n", sizeof(foo));
	printf("sizeof(bar) == %d\n", sizeof(bar));
	printf("sizeof(*bar) == %d\n", sizeof(*bar));
	return 0;
}
```

The output of this, on a 32-bit system, is```
sizeof(foo) == 4
sizeof(bar) == 4
sizeof(*bar) == 108 
```

---

### Post by LaRoza on 2008-02-27
> **Wybiral said:**
> It's true.



It's not "malloc" that has a problem, it's "sizeof".

EDIT:

I removed my explanation since this is a challenge :)

I see the issue now, I think.

(For the record, we can view edit histories...But I am not going to)

---

### Post by Wybiral on 2008-02-27
> **LaRoza said:**
> (For the record, we can view edit histories...But I am not going to)

That's somewhat creepy... (especially since I type like a drunk early in the morning, I have no idea what I'm saying)

---

### Post by LaRoza on 2008-02-27
> **Wybiral said:**
> That's somewhat creepy... (especially since I type like a drunk early in the morning, I have no idea what I'm saying)

I have never been drunk, but my early morning code can be...interesting.

The code here isn't so bad, considering I wrote it first thing.

(I think my code is a little cryptic, especially the printFraction function)

---

### Post by dwhitney67 on 2008-02-28
Here's my implementation in C++.  I have modified the original code I submitted, so that this time around I implement the Euclid algorithm for obtaining the GCD.  I also handle negative fractions as well.

Anyhow, these changes will undoubtedly disqualify me from this competition!  :(
[PHP]
#include <string>
#include <cmath>
#include <cstdlib>
#include <iostream>


class Fraction
{
  public:
    class ZeroDenominator
    {
      public:
        ZeroDenominator() {}

        std::string what() const
        {
          return "A denominator of 0 is invalid!";
        }
    };

    Fraction( int numerator = 0, int denominator = 1 ) throw( ZeroDenominator );
    Fraction( const Fraction &toCopy );

    void reciprocate() throw( ZeroDenominator );
    Fraction reciprocal() const throw( ZeroDenominator );

    double toDecimal() const;
    static Fraction fromDecimal( const double decimal, const unsigned int maxSigDigits = 5 );

    static int greatestCommonDivisor( int m, int n );

    void simplify();

    Fraction operator + ( const Fraction &rhs ) const;
    Fraction operator - ( const Fraction &rhs ) const;
    Fraction operator * ( const Fraction &rhs ) const;
    Fraction operator / ( const Fraction &rhs ) const;

    friend std::ostream & operator << ( std::ostream &os, const Fraction &f );

  private:
    int m_num;
    int m_den;
};


Fraction::Fraction( int numerator, int denominator ) throw( ZeroDenominator )
  : m_num( numerator ),
    m_den( denominator )
{
  if ( m_den == 0 )
  {
    throw ZeroDenominator();
  }

  simplify();
}

Fraction::Fraction( const Fraction &toCopy )
  : m_num( toCopy.m_num ),
    m_den( toCopy.m_den )
{
}

void
Fraction::reciprocate() throw( ZeroDenominator )
{
  int num = this->m_num;
  int den = this->m_den;

  if ( num == 0 )
  {
    throw ZeroDenominator();
  }

  this->m_num = den;
  this->m_den = num;
}

Fraction
Fraction::reciprocal() const throw( ZeroDenominator )
{
  return Fraction( this->m_den, this->m_num );
}

double
Fraction::toDecimal() const
{
  return (double) this->m_num / (double) this->m_den;
}

Fraction
Fraction::fromDecimal( const double decimal, const unsigned int maxSigDigits )
{
  int num = (int)(decimal * pow( 10, maxSigDigits ));
  int den = (int)(pow( 10, maxSigDigits ));

  return Fraction( num, den );
}

Fraction
Fraction::operator + ( const Fraction &rhs ) const
{
  int num = ( this->m_num * rhs.m_den ) + ( rhs.m_num * this->m_den );
  int den = this->m_den * rhs.m_den;

  return Fraction( num, den );
}

Fraction
Fraction::operator - ( const Fraction &rhs ) const
{
  int num = ( this->m_num * rhs.m_den ) - ( rhs.m_num * this->m_den );
  int den = this->m_den * rhs.m_den;

  return Fraction( num, den );
}

Fraction
Fraction::operator * ( const Fraction &rhs ) const
{
  int num = this->m_num * rhs.m_num;
  int den = this->m_den * rhs.m_den;

  return Fraction( num, den );
}

Fraction
Fraction::operator / ( const Fraction &rhs ) const
{
  int num = this->m_num * rhs.m_den;
  int den = this->m_den * rhs.m_num;

  return Fraction( num, den );
}

int
Fraction::greatestCommonDivisor( int m, int n )
{
  // Euclid algorithm
  if ( m % n == 0 )
  {
    return n;
  }

  return greatestCommonDivisor( n, m % n );
}

void
Fraction::simplify()
{
  const int gcd = greatestCommonDivisor( abs(this->m_num), this->m_den );

  this->m_num /= gcd;
  this->m_den /= gcd;
}

std::ostream &
operator << ( std::ostream &os, const Fraction &f )
{
  os << f.m_num << "/" << f.m_den;
  return os;
}


int main( int argc, char **argv )
{
  try
  {
    Fraction f1( 5, 10 );
    Fraction f2( 3, 7 );

    std::cout << "f1 = " << f1 << std::endl;
    std::cout << "f2 = " << f2 << std::endl;
    std::cout << "f1 + f2 = " << f1 + f2 << std::endl;
    std::cout << "f1 - f2 = " << f1 - f2 << std::endl;
    std::cout << "f1 * f2 = " << f1 * f2 << std::endl;
    std::cout << "f1 / f2 = " << f1 / f2 << std::endl;

    std::cout << "f1 as decimal = " << f1.toDecimal() << std::endl;
    std::cout << "f2 as decimal = " << f2.toDecimal() << std::endl;

    std::cout << "1.333 as a fraction = " << Fraction::fromDecimal( 1.333 ) << std::endl;

    Fraction f3( 3, 10 );
    std::cout << "f3 = " << f3 << std::endl;
    f3.reciprocate();
    std::cout << "After reciprocating f3..." << std::endl;
    std::cout << "f3 = " << f3 << std::endl;

    Fraction f4( 1, 2 );
    Fraction f5( 3, 4 );

    std::cout << "f4 = " << f4 << std::endl;
    std::cout << "f5 = " << f5 << std::endl;
    std::cout << "f4 - f5 = " << f4 - f5 << std::endl;

    Fraction f6;
    std::cout << "f6 = " << f6 << std::endl;
    std::cout << "Attempting to get reciprocal of f6..." << std::endl;
    std::cout << "reciprocal of f6 = " << f6.reciprocal() << std::endl;
  }
  catch ( Fraction::ZeroDenominator &zd )
  {
    std::cout << "Exception thrown: " << zd.what() << std::endl;
  }

  return 0;
}
[/PHP]

---

### Post by Martin Witte on 2008-02-28
Here's my final code in Python for this challenge, it now implements all behaviour as asked for by Lster
[PHP]class FractionError(Exception):
    pass

class Fraction(object):
    """Class implements fractions
    supported operations:
    - Creation of a new fraction, e.g. f = Fraction(1, 2)
    - printing of a fraction, e.g. print f ('1/2')
    - comparing of fractions with other fractions and with integers, e.g.
      Fraction(6, 4) == Fraction(3, 2), Fraction(3, 2) != Fraction(1, 2),
      Fraction(9, 3) == 3, 3 == Fraction(3, 1)
    - Multiplication, addition, division, subtraction of fractions with
      other fractions and with integers, e.g.
      Fraction(1, 2) * Fraction(1, 2) == Fraction(1, 4),
      Fraction(1, 8) * 2 == fraction(1, 4)
      Fraction(1, 3) + Fraction(2, 3) == 1
    - Create a reciproke, e.g. 'print Fraction(3, 4).reciproke()'
      will print '4/3'
    - convert a fraction to a float, by a calling float(Fraction(3, 4))
    """
    def __init__(self, numerator, denominator):
        if denominator == 0:
            raise ZeroDivisionError
        if isinstance(numerator, float) or isinstance(denominator, float):
            raise FractionError('floats not supported for numerator/denominator')
        self.numerator = numerator
        self.denominator = denominator

        def greatest_common_divisor(m, n):
            """Euclid algorithm"""
            if m % n == 0:
                return n
            else:
                return greatest_common_divisor(n, m % n)

        gcd = greatest_common_divisor(numerator, denominator)
        self.simplified_numerator = numerator / gcd
        self.simplified_denominator = denominator / gcd
        
    def __mul__(self, other):
        if isinstance(other, Fraction):
            product = Fraction(self.numerator*other.numerator, \
                               self.denominator*other.denominator)
            return Fraction(product.simplified_numerator, \
                            product.simplified_denominator)
        elif isinstance(other, int) or isinstance(other, long):
            product = Fraction(self.numerator*other, self.denominator)
            return Fraction(product.simplified_numerator, \
                            product.simplified_denominator)            
        else:
            raise FractionError('can not multiply %s with Fraction %s' %\
                                 (other, self))
    __rmul__ = __mul__

    def __float__(self):
        return (1.0 * self.numerator) / self.denominator
        
    def __str__(self):
        return "%d/%d" % (self.numerator, self.denominator)

    def __eq__(self, other):            
        if isinstance(other, Fraction):
            if self.simplified_numerator == other.simplified_numerator and \
               self.simplified_denominator == other.simplified_denominator:
                return True
            else:
                return False
        elif isinstance(other, int) or isinstance(other, long):
            if self.numerator / self.denominator == other and \
               self.numerator % self.denominator == 0:
                return True
            else:
                return False
        else:
            raise FractionError('can not compare %s with Fraction %s' %\
                                 (other, self))

    def reciproke(self):
        return Fraction(self.simplified_denominator, self.simplified_numerator)

    def __add__(self, other):
        if isinstance(other, int) or isinstance(other, long):
            other = Fraction(other, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not add %s to Fraction %s' %\
                                 (other, self))
        summation = Fraction(self.numerator * other.denominator + \
                             self.denominator * other.numerator,\
                             self.denominator * other.denominator)
        return Fraction(summation.simplified_numerator,\
                        summation.simplified_denominator)
    
    __radd__ = __add__

    def __neg__(self):
        return -1*self

    def __sub__(self, other):
        return self + (-other)

    def __rsub__(self, other):
        if isinstance(other, int) or isinstance(other, long):
            other = Fraction(other, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not add %s to Fraction %s' %\
                                 (other, self))
        difference = Fraction(other.numerator * self.denominator - \
                              other.denominator * self.numerator,\
                              other.denominator * self.denominator)

        return Fraction(difference.simplified_numerator,\
                        difference.simplified_denominator)

    def __div__(self, other):
        if isinstance(other, int) or isinstance(other, long):
            other = Fraction(other, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not divide %s by Fraction %s' %\
                                 (other, self))        
        return self * other.reciproke()

    def __rdiv__(self, other):
        if isinstance(self, int) or isinstance(self, long):
            self = Fraction(self, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not divide %s by Fraction %s' %\
                                 (other, self))        
        return other * self.reciproke()

precision = 17
eps = 1.0/10**precision

def frac(f):
    """convert argument f to a Fraction
       used http://en.wikipedia.org/wiki/Recurring_decimal for algorithm
    """
    if f * 10** (precision-2) - int(f * 10** (precision-2)) == 0:
        fr =  Fraction(int(f * 10** (precision-2)), 10** (precision-2))
    else:
        fr = None
        for i in range(1, precision):
            ten_f = (10.0**i) * f
            nine_f = ten_f - f
            if abs(nine_f - int(nine_f + eps)) < eps:
                fr = Fraction(int(nine_f + eps), int('9'*i))
                break
        
    if isinstance(fr, Fraction):
        return Fraction(fr.simplified_numerator,fr.simplified_denominator)
    else:
        raise FractionError('can not convert %s to a Fraction' % str(f))

if __name__ == '__main__':
    import unittest, operator
    class FractionTestCase(unittest.TestCase):
        def testInit(self):
            self.assertRaises(ZeroDivisionError, Fraction, 1, 0)
            self.assertRaises(FractionError, Fraction, 1.2, 8)
            self.assertRaises(FractionError, Fraction, 8, 1.2)
            
        def testPrint(self):
            self.assertEqual(str(Fraction(1,2)), '1/2')
        
        def testEquality(self):
            self.assertEqual(Fraction(3,2), Fraction(3,2))
            self.assertEqual(Fraction(3,2), Fraction(6,4))
            self.assertEqual(Fraction(4,2), 2)
            self.assertEqual(2, Fraction(4,2))
            self.assertNotEqual(1, Fraction(4, 3))
            self.assertNotEqual(Fraction(5, 4), Fraction(4, 3))
            self.assertRaises(FractionError, cmp, Fraction(1, 2), 1.2)
            self.assertRaises(FractionError, cmp, -0.2, Fraction(1, 2))

        def testMultiplication(self):
            self.assertEqual(Fraction(3, 2) * Fraction(3, 2), Fraction(9, 4))
            self.assertEqual(Fraction(1,3) * 2, Fraction(2, 3))
            self.assertEqual(Fraction(1,8) * 2, Fraction(1, 4))
            self.assertEqual(2 * Fraction(1,3), Fraction(2, 3))
            self.assertRaises(FractionError, operator.mul, Fraction(1,4), 2.33)

        def testReciproke(self):
            self.assertEqual(Fraction(7,3), Fraction(3,7).reciproke())
            self.assertNotEqual(Fraction(7,3), Fraction(3,8).reciproke())
            self.assertEqual(Fraction(7,3), Fraction(6,14).reciproke())
            
        def testFloat(self):
            self.assertEqual(float(Fraction(3, 4)), 0.75)
            self.assertEqual(float(Fraction(5, 4)), 1.25)
            self.assertNotEqual(float(Fraction(5, 4)), 1.250001)

        def testAddition(self):
            self.assertEqual(Fraction(1, 4) + Fraction(1, 4), Fraction(1, 2))
            self.assertEqual(Fraction(1, 2) + Fraction(1, 2), 1)
            self.assertNotEqual(Fraction(3, 4) + Fraction(1, 2), 1)
            self.assertEqual(1, Fraction(3, 4) + Fraction(2, 8))
            self.assertRaises(FractionError, operator.add, Fraction(1,4), 2.33)

        def testSubtraction(self):
            self.assertEqual(Fraction(1, 4) - Fraction(1, 8), Fraction(1, 8))
            self.assertEqual(Fraction(1, 2) - Fraction(1, 2), 0)
            self.assertNotEqual(Fraction(3, 4) - Fraction(1, 2), 0)
            self.assertEqual(1, Fraction(5, 4) - Fraction(2, 8))
            self.assertEqual(Fraction(7, 4) - Fraction(3, 4), 1)
            self.assertEqual(Fraction(3, 4), 1 - Fraction(2, 8))
            self.assertRaises(FractionError, operator.sub, Fraction(1,4), 2.33)

        def testDivision(self):
            self.assertEqual(5 / Fraction(1, 2), 10)
            self.assertEqual(Fraction(2, 3) / Fraction(2, 5), Fraction(5, 3))
            self.assertEqual(Fraction(2, 3) / 2, Fraction(1, 3))
            self.assertRaises(FractionError, operator.div, Fraction(1,4), 2.33)

        def testDecimalToFractionconversion(self):
            self.assertEqual(frac(0.25), Fraction(1, 4))
            self.assertEqual(frac(1.25), Fraction(5, 4))
            self.assertEqual(frac(0.375), Fraction(3, 8))
            self.assertEqual(frac(0.375), Fraction(3, 8))
            self.assertEqual(frac(0.4375), Fraction(7, 16))
            self.assertEqual(frac(0.9921875), Fraction(127, 128))
            self.assertEqual(frac(0.9990234375), Fraction(1023, 1024))
            self.assertEqual(frac(0.333333333333333), Fraction(int('3'*15), 10**15))
            self.assertEqual(frac(0.3333333333333333), Fraction(1, 3))
            self.assertEqual(frac(0.18181818181818181), Fraction(2, 11))
            self.assertEqual(frac(0.076923076923076923), Fraction(1, 13))
            self.assertEqual(frac(0.23076923076923076923), Fraction(3, 13))
            self.assertEqual(frac(0.14285714285714285), Fraction(1, 7))
            self.assertEqual(frac(0.05882352941176470), Fraction(1, 17))
            # However....
            # 1/29
            self.assertRaises(FractionError, frac, 0.0344827586206896551724137931)
            
    suite = unittest.TestLoader().loadTestsFromTestCase(FractionTestCase)
    unittest.TextTestRunner(verbosity=2).run(suite)
[/PHP]

---

### Post by mssever on 2008-02-28
Here's my submission, in Ruby. Ruby's Rational class already does this, but I wrote my Fraction class without reference to Rational (my unit tests use Rational, however, to simplify testing). I also stuck to only what's available in Ruby without require-ing anything.

Features:[LIST]
[*]Signed fractions
[*]Math: addition, subtraction, multiplication, division, absolute value; No special conversions or operators required.
[*]Comparisons: <, <=, ==, !=, =>, >, between? (the question mark is part of the method name, in good Ruby style)
[*]Reciprocol, reduction (both destructive and non-destructive)
[*]Type conversions to and from strings, ints and floats. For conversion to string, both strict fractions (3/2) and mixed fractions (1 1/2) are available.
[*]New fractions are reduced by default. However, if you pass false as the third paramater to Fraction.new, it won't be automatically reduced. There are situations where it's useful to keep fractions in an un-reduced form.[/LIST]fractions.rb:
```
class Integer
  def to_frac
    Fraction.new(self,1,false)
  end
end

class Float
  def to_frac #Some ideas for this method shamelessly stolen from wybiral
    float_str = to_s
    /([0-9]*)\.([0-9]*)/.match float_str
    whole = $1.to_i.to_frac
    frac = Fraction.new($2.to_i,10 ** $2.length)
    whole + frac
  end
end

class String
  def to_frac
    if strip =~ /^([0-9-]* )?([0-9-]+)[\s]*\/[\s]*([0-9]+)$/
      whole = $1.to_i
      numerator = $2.to_i
      denominator = $3.to_i
      Fraction.new(numerator, denominator) + whole.to_frac
    elsif to_f != 0
      to_f.to_frac
    else
      Fraction.new 0,1
    end
  end
end

class InvalidNumeratorOrDenominatorError < StandardError
end

class Fraction
  include Comparable

  def initialize(numerator, denominator = 1, reduce_this = true)
    raise ZeroDivisionError if denominator == 0
    @negative = false
    [numerator, denominator].each do |i|
      raise InvalidNumeratorOrDenominatorError, i.inspect unless i.kind_of? Integer
      @negative = true if i < 0
    end
    @numerator = numerator.abs
    @denominator = denominator.abs
    reduce! if reduce_this
  end
    
  # Type casts / coersion
  def coerce(other)
    [other.to_frac, self]
  end

  def to_f
    (@numerator.to_f * sign_int) / @denominator.to_f
  end
  
  def to_frac
    self
  end
  
  def to_i
    to_f.to_i
  end
  
  def to_mixed
    return to_s if @numerator < @denominator || @denominator == 1
    whle = @numerator / @denominator #Should be caled whole, but the forum software censors the code under that name.
    numerator = @numerator - (whle * @denominator)
    return "#{sign_str}#{whle}" if numerator == 0
    "#{sign_str}#{whle} #{numerator}/#{@denominator}"
  end

  def to_s(mixed = false)
    unless mixed
      return @numerator.to_s if @denominator == 1
      "#{sign_str}#{@numerator}/#{@denominator}"
    else
      to_mixed
    end
  end
  
  def inspect
    a = "<Fraction: #{sign_str}#{@numerator}"
    a += (@denominator == 1) ? ">" : "/#{@denominator}>"
    a
  end
  
  # Info about the current instance
  attr_reader :numerator, :denominator
  def negative?
    @negative
  end
  
  # Fraction operations
  def reciprocal
    Fraction.new @denominator * sign_int, @numerator, false
  end
  
  def reduce
    factor = gcd @numerator, @denominator
    Fraction.new @numerator * sign_int / factor, @denominator / factor
  end

  def reduce!
    factor = gcd @numerator, @denominator
    @numerator = @numerator / factor
    @denominator = @denominator / factor
    self
  end
  
  def enlarge(other)
    other = other.to_frac
    @numerator * other.denominator
  end
  
  # Mathematical operations
  def abs
    Fraction.new @numerator, @denominator
  end

  def <=>(other)
    other = other.to_frac
    num1 = enlarge other
    num2 = other.enlarge self
    num1 *= sign_int
    num2 *= -1 if other.negative?
    #puts "#{self} <=> #{other}"
    #puts "num1 = #{num1}; num2 = #{num2}"
    num1 <=> num2
  end
  
  def -@ #negative fraction
    Fraction.new @numerator * -1, @denominator, false
  end
  
  alias_method :+@, :abs #positive fraction
  
  def *(other)
    other = other.to_frac
    numerator = @numerator * other.numerator
    denominator = @denominator * other.denominator
    numerator *= -1 if (negative? || other.negative?) && !(negative? && other.negative?)
    Fraction.new(numerator, denominator)
  end

  def /(other)
    self * other.to_frac.reciprocal
  end

  def +(other)
    other = other.to_frac
    num1 = enlarge other
    num2 = other.enlarge self
    num1 *= -1 if negative?
    num2 *= -1 if other.negative?
    Fraction.new(num1 + num2, @denominator * other.denominator)
  end

  def -(other)
    other = other.to_frac
    num1 = enlarge other
    num2 = other.enlarge self
    num1 *= -1 if negative?
    num2 *= -1 if other.negative?
    Fraction.new(num1 - num2, @denominator * other.denominator)
  end
  
  # Private methods
  private
  
  def sign_str
    (negative?) ? '-' : ''
  end

  def sign_int
    (negative?) ? -1 : 1
  end
    
  def gcd(a, b)
    return a if b == 0
    gcd b, a % b
  end
end
```Test suite:
```
#!/usr/bin/env ruby

require 'fractions'
require 'rational'
require 'test/unit'

class FractionTests < Test::Unit::TestCase
  def setup
    @operations = [
      [
        [1,2],
        [3,4]
      ],
      [
        [5,3],
        [3,2]
      ],
      [
        [-3,8],
        [7155,9990]
      ],
      [
        [23,-36],
        [8,1]
      ],
      [
        4,
        6
      ],
      [
        19,
        [3,6]
      ],
      [
        [6,7],
        3
      ],
      [
        [3,5],
        2.3
      ],
      [
        6.321,
        [5,2]
      ],
      [
        5.46542,
        [346,24]
      ],
    ]
  end
    
  def test_typecasts
    [[Fraction.new(1,2),'1/2'],[Fraction.new(5,7), '5/7'],[Fraction.new(25,-23), '-25/23']].each do |f|
      assert_equal f[1], f[0].to_s, "<Fraction: #{f[1]}>.to_s"
    end
    [[Fraction.new(1,2),'1/2'],[Fraction.new(8,7), '1 1/7'],[Fraction.new(25,-23), '-1 2/23']].each do |f|
      assert_equal f[1], f[0].to_mixed, "<Fraction: #{f[0]}>.to_mixed"
    end
    [[Fraction.new(1,2),0.5],[Fraction.new(3,4), 0.75],[Fraction.new(9,4), 2.25]].each do |f|
      assert_equal f[1], f[0].to_f, "<Fraction: #{f[0]}>.to_f"
    end
    assert_equal Fraction.new(4,1), 4.to_frac, '4.to_frac'
    assert_equal Fraction.new(1,4), 0.25.to_frac, '0.25.to_frac'
    assert_equal Fraction.new(3,2), 1.5.to_frac, '1.5.to_frac'
    assert_equal Fraction.new(1,2), '1/2'.to_frac, '"1/2".to_frac'
    assert_equal Fraction.new(1,2), '1 / 2'.to_frac, '"1 / 2".to_frac'
    assert_equal Fraction.new(-1,2), '-1/2'.to_frac, '"-1/2".to_frac'
    assert_equal Fraction.new(3,2), '1 1/2'.to_frac, '"1 1/2".to_frac'
    assert_equal Fraction.new(2,1), '2'.to_frac, '"2".to_frac'
    assert_equal Fraction.new(0,1), 'foo/bar'.to_frac, '"foo/bar".to_frac'
    assert_equal Fraction.new(5,2), '2.5'.to_frac, '"2.5".to_frac'
  end
  
  def test_math
    @operations.each do |f|
      if f[0].respond_to? :length
        f1 = Fraction.new *f[0]
        r1 = Rational *f[0]
      else
        f1 = f[0]
        r1 = f[0]
      end
      if f[1].respond_to? :length
        f2 = Fraction.new *f[1]
        r2 = Rational *f[1]
      else
        f2 = f[1]
        r2 = f[1]
      end

      f_sum = f1 + f2
      f_diff = f1 - f2
      f_prod = f1 * f2
      f_quo = f1 / f2
      r_sum = r1 + r2
      r_diff = r1 - r2
      r_prod = r1 * r2
      r_quo = r1 / r2
      
      assert_equal r_sum.to_f.to_s, f_sum.to_f.to_s, "#{f1} + #{f2}"
      assert_equal r_diff.to_f.to_s, f_diff.to_f.to_s, "#{f1} - #{f2}"
      assert_equal r_prod.to_f.to_s, f_prod.to_f.to_s, "#{f1} * #{f2}"
      assert_equal r_quo.to_f.to_s, f_quo.to_f.to_s, "#{f1} / #{f2}"
    end
  end
  
  def test_comparison
    assert_equal Fraction.new(1,2), Fraction.new(4,8,false)
    assert_equal Fraction.new(2,3), Fraction.new(4,6)
    assert_equal Fraction.new(-9,5), Fraction.new(27,-15,false)
  end
  
  def test_sign
    a = Fraction.new(1,2)
    b = Fraction.new(-1,2)
    c = Fraction.new(1,-2)
    assert_not_equal a.to_s, b.to_s
    assert_not_equal a.to_s, c.to_s
    assert_not_equal a.to_f, b.to_f
    assert_not_equal a.to_f, c.to_f
    assert_not_equal a, b
    assert_not_equal a, c
    assert_equal b, c
  end
  
  def test_creation_and_reduction
    assert_equal Fraction.new(1,2).numerator, Fraction.new(1,2).numerator
    assert_equal Fraction.new(1,2).numerator, Fraction.new(2,4).numerator
    assert_not_equal Fraction.new(2,4).numerator, Fraction.new(2,4,false).numerator
  end
  
  def test_sign_changes
    fractions = [[Fraction.new(4,5),   Fraction.new(-4,5)],
                 [Fraction.new(3,2),   Fraction.new(-3,2)],
                 [Fraction.new(-9,27), Fraction.new(9,27)],
                 [Fraction.new(-2,3),  Fraction.new(2,3)],
                ]
    fractions.each do |f|
      a = f[0]
      b = f[1]
      assert_not_equal a, b
      assert_equal +a, +b
      assert_equal -a, -b
      if a > 0
        assert_equal a, +b
        assert_equal -a, b
      else
        assert_equal a, -b
        assert_equal +a, b
      end
    end
  end
end
```Here's an example irb session to demonstrate the class. Notice how straightforward math operations are. Just use the standard operations.
```
~/programming/snippets/fractions:$ irb
>> require 'fractions'
=> true
>> a = Fraction.new 1,2
=> <Fraction: 1/2>
>> -a
=> <Fraction: -1/2>
>> b = Fraction.new 2,6
=> <Fraction: 1/3>
>> b.to_s
=> "1/3"
>> a + b
=> <Fraction: 5/6>
>> "#{a + b}"
=> "5/6"
>> "#{a / 2 + b}"
=> "7/12"
>> (a + 5 + b).to_s
=> "35/6"
>> (a + 5 + b).to_mixed
=> "5 5/6"
>> a *= -1
=> <Fraction: -1/2>
>> 3.5 + b
=> <Fraction: 23/6>
>> c = (3.5 + b).reciprocal
=> <Fraction: 6/23>
>> c * c.reciprocal
=> <Fraction: 1>
>> a < b
=> false
>> Fraction.new(1,2) == 0.5
=> true
```

---

### Post by DemonDomen on 2008-02-28
Can I use the time library in python?
All the math functions are made from scratch, I just need something to pause it.

---

### Post by Lster on 2008-02-28
[QUOTE=DemonDomen]Can I use the time library in python?[/QUOTE]

Yes, you can. But I'm not quite sure why you would want to... :)

All the entries so far are very good - and it's only Thursday. I'm going to have a hard time choosing, evidently!

---

### Post by LaRoza on 2008-02-28
> **Lster said:**
> 
All the entries so far are very good - and it's only Thursday. I'm going to have a hard time choosing, evidently!

You don't need to be nice, mine is bad.

---

### Post by Lster on 2008-02-28
[QUOTE=LaRoza]You don't need to be nice, mine is bad.[/QUOTE]

I was being sincere - you are too modest LaRoza. ;) I can't really voice my opinions until after the competition is over, but your design is not fundamentally different from how I would go about this. :)

---

### Post by DemonDomen on 2008-02-28
> **Lster said:**
> Yes, you can. But I'm not quite sure why you would want to... :)

All the entries so far are very good - and it's only Thursday. I'm going to have a hard time choosing, evidently!

I was making a program, but now I noticed that I only needed to make a library.

Here's the code:
EDIT: It's in python
EDIT2: I made the simplify function a little better.

```
fractions = []
numerator = 0
denominator = 0
class fraction:
	def gcd(self,a,b):
		if not b:
			return a
		else:
			return self.gcd(b, a % b)
	def create(self,numerator,denominator):
		global fractions
		self.numerator = numerator
		self.denominator = denominator
		join_numbers = str(self.numerator)+"/"+str(self.denominator)
		fractions.append([self.numerator,self.denominator])
		print "The fraction",join_numbers,"has been added"
	def list_fractions(self):
		if len(fractions):
			for i in range(len(fractions)):
				count = i+1
				print str(count)+".", fractions[i][0] + "/" + fractions[i][1]
		else:
			print "There are no fractions in the list"
	def multiply(self,fr1,fr2):
		fra1 = int(fr1)
		fra2 = int(fr2)
		fra1 -= 1
		fra2 -= 1
		try:
			mult_numerator = int(fractions[fra1][0])*int(fractions[fra2][0])
			mult_denominator = int(fractions[fra1][1])*int(fractions[fra2][1])
			return str(mult_numerator) + "/" + str(mult_denominator)
		except IndexError:
			print "The fractions are not in the list"
	def output(self,numerator,denominator):
		print "The fraction is", numerator + "/" + denominator
	def reciprocal(self,fr):
		fra = int(fr)-1
		input_user = fractions[fra]
		numerator = input_user[0]
		denominator = input_user[1]
		return denominator+"/"+numerator
	def add(self,fr1,fr2):
		fra1 = int(fr1)
		fra2 = int(fr2)
		fra1 -= 1
		fra2 -= 1
		try:
			denominator_mult = int(fractions[fra1][1])*int(fractions[fra2][1])
			numerator1 = int(fractions[fra1][0])*int(denominator_mult)
			numerator2 = int(fractions[fra2][0])*int(denominator_mult)
			numerator_add = numerator1+numerator2
			return str(numerator_add)+"/"+str(denominator_mult)
		except IndexError:
			print "The fractions are not in the list"
	def subtract(self,fr1,fr2):
		fra1 = int(fr1)
		fra2 = int(fr2)
		fra1 -= 1
		fra2 -= 1
		try:
			denominator_mult = int(fractions[fra1][1])*int(fractions[fra2][1])
			numerator1 = int(fractions[fra1][0])*int(denominator_mult)
			numerator2 = int(fractions[fra2][0])*int(denominator_mult)
			numerator_add = numerator1-numerator2
			return str(numerator_add)+"/"+str(denominator_mult)
		except IndexError:
			print "The fractions are not in the list"
	def division(self,fr1,fr2):
		fra1 = int(fr1)
		fra2 = int(fr2)
		fra1 -= 1
		fra2 -= 1
		try:
			dev_numerator = int(fractions[fra1][0])*int(fractions[fra2][1])
			dev_denominator = int(fractions[fra1][1])*int(fractions[fra2][0])
			return str(dev_numerator)+"/"+str(dev_denominator)
		except IndexError:
			print "The fractions are not in the list"
	def simplify(self,fraction):
		global numerator
		global denominator
		values = fraction.split('/')
		numerator = int(values[0])
		denominator = int(values[1])
		numerator_out = numerator / self.gcd(numerator,denominator)
		denominator_out = denominator / self.gcd(numerator,denominator)
		if numerator_out == denominator_out:
			return "1"
		elif denominator_out == 1:
			return str(numerator_out)
		else:
			return str(numerator_out)+"/"+str(denominator_out)
		numerator = 0
		denominator = 0
	def decimal(self,fr):
		fra = int(fr)-1
		try:
			input_user = fractions[fra]
			numerator = input_user[0]
			denominator = input_user[1]
			float_fraction = int(numerator)/int(denominator)
			return int(round(float_fraction))
		except IndexError:
			print "not in the list"
	def fraction(self,decimal_in):
		self.output = ''
		if '.' not in decimal_in:
			self.output = decimal_in+"/1"
		else:
			split_string = decimal_in.split('.')
			zero = '0' * len(split_string[1])
			numerator = split_string[1]
			denominator = '1' + zero
			whole = int(split_string[0])*int(denominator)
			numerator_top = int(whole)+int(numerator)
			self.output = str(numerator_top)+"/"+denominator
		return self.output

```

---

### Post by Lux Perpetua on 2008-02-29
This is mainly for entertainment. Here is a mostly compile-time fraction library in C++: ```
#ifndef FRACTION_HPP
#define FRACTION_HPP

/* fractions.hpp
 * (Mostly) compile-time fraction library.
 */

// Greatest common divisor (GCD) of two positive integers.
// The GCD can be retrieved via the static const member variable `value'.
// This is a direct implementation of Euclid's algorithm.
template<unsigned int N, unsigned int M>
struct gcd_u : public gcd_u<M % N, N> 
{ };

// Euclid's algorithm, basis case.
template< >
template<unsigned int M>
struct gcd_u<0, M> {
    static const int value = M;
};

// GCD of two arbitrary integers.
template<int N, int M>
struct gcd : public gcd_u<(N < 0)? -N:N, (M < 0)? -M:M> 
{ };

// In this library, a "fraction" is a subtype of an instantiation of
// this template. Note that an instance of a fraction type has no data
// members; it is the type itself that carries all the information.
// (Reading the example program might help if you're confused.)
template<int N, int M>
struct fraction {
    static const int num = ((M < 0)? -N:N)/gcd<N, M>::value;
    static const int den = ((M < 0)? -M:M)/gcd<N, M>::value;
};

// Product of two fractions.
template<typename F0, typename F1>
struct fraction_multiply : public fraction <
    (F0::num/gcd<F0::num, F1::den>::value)
        * F1::num/gcd<F1::num, F0::den>::value,
    (F0::den/gcd<F1::num, F0::den>::value)
        * F1::den/gcd<F0::num, F1::den>::value>
{ };

// Reciprocal of a fraction.
template<typename F>
struct fraction_invert : public fraction<F::den, F::num> 
{ };

// Quotient of two fractions.
template<typename F0, typename F1>
struct fraction_divide : public fraction_multiply<F0, fraction_invert<F1> > 
{ };

// Sum of two fractions.
template<typename F0, typename F1>
struct fraction_add : public fraction <
    F0::num * (F1::den/gcd<F0::den, F1::den>::value)
    + F1::num * (F0::den/gcd<F0::den, F1::den>::value),
    F0::den * (F1::den/gcd<F0::den, F1::den>::value)>
{ };

// Opposite of a fraction.
template<typename F>
struct fraction_negate : public fraction<-F::num, F::den> 
{ };

// Difference of two fractions.
template<typename F0, typename F1>
struct fraction_subtract : public fraction_add<F0, fraction_negate<F1> > 
{ };

// Three-valued predicate (like strcmp). The sign of value is the sign
// of F0 - F1. Note that fractions in this library always have positive
// denominators.
template<typename F0, typename F1>
struct compare_fractions {
    static const int value = F0::num * F1::den - F1::num * F0::den;
};

// I don't know how to compute a textual representation of a fraction
// during compilation, so this is a normal function that runs at runtime.
template<typename F>
void print_fraction() {
    std::cout << F::num << "/" << F::den << std::endl;
}

// This also runs at runtime, but it's mainly for testing, so it doesn't
// really count.
template<typename F0, typename F1>
void print_compare_fractions() {
    if (compare_fractions<F0, F1>::value < 0)
        std::cout << "less";
    else if (compare_fractions<F0, F1>::value > 0)
        std::cout << "greater";
    else
        std::cout << "equal";
    std::cout << std::endl;
}

#endif

```Example program:```
#include <iostream>
#include "fractions.hpp"

int main(void) {
    // Note that we do not create any instances; we only instantiate
    // types. Instances of these types are actually useless, since
    // they carry no data. 
    typedef fraction<84, -144> F0;
    typedef fraction<1, -4> F1;
    typedef fraction_subtract<F0, F1> F2;
    typedef fraction_divide<fraction<4, -5>, fraction<4, 5> > F3;

    print_fraction<F0>();
    print_fraction<F1>();
    print_fraction<F2>();
    print_fraction<F3>();

    print_compare_fractions<F0, F3>();
    print_compare_fractions<F0, fraction_add<F1, F2> >();

    return 0;
}
```I may do another submission later if I can get around to it.

---

### Post by aks44 on 2008-02-29
Good job Lux Perpetua! ;)


Here's my submission (C++ this time).

EDIT: I forgot to mention that it fulfils all the original specifications, and a bit more. ;)

Point of interest: all operations CAN BE overflow-proof (but you don't have to pay for it if you don't want to).

This class is fairly complete (accepts LHS integer operations, ...) but still has a few quirks. Namely, it doesn't support implicit double operations because of the ambiguities a double conversion-constructor would introduce, so you have to use the FromDouble() factory.

I tried to document it as much as possible, especially when it comes to language constructs or specific algorithms.

```
$ ./test.sh
Basic examples:
3
3/2
1 1/2

Operations:
1 1/2
3/2
817696623/260280919

Error-checking:
FractionError::DivByZero
FractionError::Overflow

Error-checking now DISABLED:
9223372036854775805/2
```



[SIZE="3"]**ERRATA:**[/SIZE]

In **SafeInt :: Div** implementation (at the bottom of fraction.h), the code should be:
```
template<bool safe, class T> T SafeInt::Div(const T a, const T b)
{
  // TODO: static assertions against T
  if (safe)
  {  // THIS BRACKET WAS MISSING FROM THE ORIGINAL SUBMISSION
    if (b == 0)
      throw FractionError::DivByZero();
    if (  (a == std::numeric_limits<T>::min())
        &&(b == -1))
      throw FractionError::Overflow();
  }; // THIS BRACKET WAS MISSING FROM THE ORIGINAL SUBMISSION

  return a / b;
}
```
I uploaded a corrected archive.

---

### Post by Lux Perpetua on 2008-02-29
> **aks44 said:**
> Good job Lux Perpetua! ;)Thank you. Regarding your code: I was wondering when somebody would implement a decent decimal-to-fraction facility. :-) If you want good rational approximations of a number, continued fractions are the only game in town, as far as I know.

---

### Post by aks44 on 2008-02-29
> **Lux Perpetua said:**
> Regarding your code: I was wondering when somebody would implement a decent decimal-to-fraction facility. :-) If you want good rational approximations of a number, continued fractions are the only game in town, as far as I know.

Well, it relieves me that continued fractions are a "well-known" method...
My own implementation was as naive as the other participants', but seeing the crappy results (denominator way too big) I decided to research the question...
Now I don't feel "cheating" anymore... ;) (I'm way past the "homework" stage though, as a programmer my job includes finding good solutions even if they're not "innovative")

---

### Post by Lster on 2008-02-29
After this is challenge is over I will post my own method, using a similar algorithm. I see what Wybiral meant - it is more fun to participate than judge! ;)

---

### Post by seventhc on 2008-02-29
> **Martin Witte said:**
> Here's my final code in Python for this challenge, it now implements all behaviour as asked for by Lster
[php]class FractionError(Exception):
    pass

class Fraction(object):
    """Class implements fractions
    supported operations:
    - Creation of a new fraction, e.g. f = Fraction(1, 2)
    - printing of a fraction, e.g. print f ('1/2')
    - comparing of fractions with other fractions and with integers, e.g.
      Fraction(6, 4) == Fraction(3, 2), Fraction(3, 2) != Fraction(1, 2),
      Fraction(9, 3) == 3, 3 == Fraction(3, 1)
    - Multiplication, addition, division, subtraction of fractions with
      other fractions and with integers, e.g.
      Fraction(1, 2) * Fraction(1, 2) == Fraction(1, 4),
      Fraction(1, 8) * 2 == fraction(1, 4)
      Fraction(1, 3) + Fraction(2, 3) == 1
    - Create a reciproke, e.g. 'print Fraction(3, 4).reciproke()'
      will print '4/3'
    - convert a fraction to a float, by a calling float(Fraction(3, 4))
    """
    def __init__(self, numerator, denominator):
        if denominator == 0:
            raise ZeroDivisionError
        if isinstance(numerator, float) or isinstance(denominator, float):
            raise FractionError('floats not supported for numerator/denominator')
        self.numerator = numerator
        self.denominator = denominator

        def greatest_common_divisor(m, n):
            """Euclid algorithm"""
            if m % n == 0:
                return n
            else:
                return greatest_common_divisor(n, m % n)

        gcd = greatest_common_divisor(numerator, denominator)
        self.simplified_numerator = numerator / gcd
        self.simplified_denominator = denominator / gcd
        
    def __mul__(self, other):
        if isinstance(other, Fraction):
            product = Fraction(self.numerator*other.numerator, \
                               self.denominator*other.denominator)
            return Fraction(product.simplified_numerator, \
                            product.simplified_denominator)
        elif isinstance(other, int) or isinstance(other, long):
            product = Fraction(self.numerator*other, self.denominator)
            return Fraction(product.simplified_numerator, \
                            product.simplified_denominator)            
        else:
            raise FractionError('can not multiply %s with Fraction %s' %\
                                 (other, self))
    __rmul__ = __mul__

    def __float__(self):
        return (1.0 * self.numerator) / self.denominator
        
    def __str__(self):
        return "%d/%d" % (self.numerator, self.denominator)

    def __eq__(self, other):            
        if isinstance(other, Fraction):
            if self.simplified_numerator == other.simplified_numerator and \
               self.simplified_denominator == other.simplified_denominator:
                return True
            else:
                return False
        elif isinstance(other, int) or isinstance(other, long):
            if self.numerator / self.denominator == other and \
               self.numerator % self.denominator == 0:
                return True
            else:
                return False
        else:
            raise FractionError('can not compare %s with Fraction %s' %\
                                 (other, self))

    def reciproke(self):
        return Fraction(self.simplified_denominator, self.simplified_numerator)

    def __add__(self, other):
        if isinstance(other, int) or isinstance(other, long):
            other = Fraction(other, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not add %s to Fraction %s' %\
                                 (other, self))
        summation = Fraction(self.numerator * other.denominator + \
                             self.denominator * other.numerator,\
                             self.denominator * other.denominator)
        return Fraction(summation.simplified_numerator,\
                        summation.simplified_denominator)
    
    __radd__ = __add__

    def __neg__(self):
        return -1*self

    def __sub__(self, other):
        return self + (-other)

    def __rsub__(self, other):
        if isinstance(other, int) or isinstance(other, long):
            other = Fraction(other, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not add %s to Fraction %s' %\
                                 (other, self))
        difference = Fraction(other.numerator * self.denominator - \
                              other.denominator * self.numerator,\
                              other.denominator * self.denominator)

        return Fraction(difference.simplified_numerator,\
                        difference.simplified_denominator)

    def __div__(self, other):
        if isinstance(other, int) or isinstance(other, long):
            other = Fraction(other, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not divide %s by Fraction %s' %\
                                 (other, self))        
        return self * other.reciproke()

    def __rdiv__(self, other):
        if isinstance(self, int) or isinstance(self, long):
            self = Fraction(self, 1)
        if not (isinstance(other, int) or isinstance(other, long) or \
                isinstance(other, Fraction)):
            raise FractionError('can not divide %s by Fraction %s' %\
                                 (other, self))        
        return other * self.reciproke()

precision = 17
eps = 1.0/10**precision

def frac(f):
    """convert argument f to a Fraction
       used http://en.wikipedia.org/wiki/Recurring_decimal for algorithm
    """
    if f * 10** (precision-2) - int(f * 10** (precision-2)) == 0:
        fr =  Fraction(int(f * 10** (precision-2)), 10** (precision-2))
    else:
        fr = None
        for i in range(1, precision):
            ten_f = (10.0**i) * f
            nine_f = ten_f - f
            if abs(nine_f - int(nine_f + eps)) < eps:
                fr = Fraction(int(nine_f + eps), int('9'*i))
                break
        
    if isinstance(fr, Fraction):
        return Fraction(fr.simplified_numerator,fr.simplified_denominator)
    else:
        raise FractionError('can not convert %s to a Fraction' % str(f))

if __name__ == '__main__':
    import unittest, operator
    class FractionTestCase(unittest.TestCase):
        def testInit(self):
            self.assertRaises(ZeroDivisionError, Fraction, 1, 0)
            self.assertRaises(FractionError, Fraction, 1.2, 8)
            self.assertRaises(FractionError, Fraction, 8, 1.2)
            
        def testPrint(self):
            self.assertEqual(str(Fraction(1,2)), '1/2')
        
        def testEquality(self):
            self.assertEqual(Fraction(3,2), Fraction(3,2))
            self.assertEqual(Fraction(3,2), Fraction(6,4))
            self.assertEqual(Fraction(4,2), 2)
            self.assertEqual(2, Fraction(4,2))
            self.assertNotEqual(1, Fraction(4, 3))
            self.assertNotEqual(Fraction(5, 4), Fraction(4, 3))
            self.assertRaises(FractionError, cmp, Fraction(1, 2), 1.2)
            self.assertRaises(FractionError, cmp, -0.2, Fraction(1, 2))

        def testMultiplication(self):
            self.assertEqual(Fraction(3, 2) * Fraction(3, 2), Fraction(9, 4))
            self.assertEqual(Fraction(1,3) * 2, Fraction(2, 3))
            self.assertEqual(Fraction(1,8) * 2, Fraction(1, 4))
            self.assertEqual(2 * Fraction(1,3), Fraction(2, 3))
            self.assertRaises(FractionError, operator.mul, Fraction(1,4), 2.33)

        def testReciproke(self):
            self.assertEqual(Fraction(7,3), Fraction(3,7).reciproke())
            self.assertNotEqual(Fraction(7,3), Fraction(3,8).reciproke())
            self.assertEqual(Fraction(7,3), Fraction(6,14).reciproke())
            
        def testFloat(self):
            self.assertEqual(float(Fraction(3, 4)), 0.75)
            self.assertEqual(float(Fraction(5, 4)), 1.25)
            self.assertNotEqual(float(Fraction(5, 4)), 1.250001)

        def testAddition(self):
            self.assertEqual(Fraction(1, 4) + Fraction(1, 4), Fraction(1, 2))
            self.assertEqual(Fraction(1, 2) + Fraction(1, 2), 1)
            self.assertNotEqual(Fraction(3, 4) + Fraction(1, 2), 1)
            self.assertEqual(1, Fraction(3, 4) + Fraction(2, 8))
            self.assertRaises(FractionError, operator.add, Fraction(1,4), 2.33)

        def testSubtraction(self):
            self.assertEqual(Fraction(1, 4) - Fraction(1, 8), Fraction(1, 8))
            self.assertEqual(Fraction(1, 2) - Fraction(1, 2), 0)
            self.assertNotEqual(Fraction(3, 4) - Fraction(1, 2), 0)
            self.assertEqual(1, Fraction(5, 4) - Fraction(2, 8))
            self.assertEqual(Fraction(7, 4) - Fraction(3, 4), 1)
            self.assertEqual(Fraction(3, 4), 1 - Fraction(2, 8))
            self.assertRaises(FractionError, operator.sub, Fraction(1,4), 2.33)

        def testDivision(self):
            self.assertEqual(5 / Fraction(1, 2), 10)
            self.assertEqual(Fraction(2, 3) / Fraction(2, 5), Fraction(5, 3))
            self.assertEqual(Fraction(2, 3) / 2, Fraction(1, 3))
            self.assertRaises(FractionError, operator.div, Fraction(1,4), 2.33)

        def testDecimalToFractionconversion(self):
            self.assertEqual(frac(0.25), Fraction(1, 4))
            self.assertEqual(frac(1.25), Fraction(5, 4))
            self.assertEqual(frac(0.375), Fraction(3, 8))
            self.assertEqual(frac(0.375), Fraction(3, 8))
            self.assertEqual(frac(0.4375), Fraction(7, 16))
            self.assertEqual(frac(0.9921875), Fraction(127, 128))
            self.assertEqual(frac(0.9990234375), Fraction(1023, 1024))
            self.assertEqual(frac(0.333333333333333), Fraction(int('3'*15), 10**15))
            self.assertEqual(frac(0.3333333333333333), Fraction(1, 3))
            self.assertEqual(frac(0.18181818181818181), Fraction(2, 11))
            self.assertEqual(frac(0.076923076923076923), Fraction(1, 13))
            self.assertEqual(frac(0.23076923076923076923), Fraction(3, 13))
            self.assertEqual(frac(0.14285714285714285), Fraction(1, 7))
            self.assertEqual(frac(0.05882352941176470), Fraction(1, 17))
            # However....
            # 1/29
            self.assertRaises(FractionError, frac, 0.0344827586206896551724137931)
            
    suite = unittest.TestLoader().loadTestsFromTestCase(FractionTestCase)
    unittest.TextTestRunner(verbosity=2).run(suite)
[/php]
I am sure it is me, something I am doing wrong...but I get an error when I run this...here is the error
```
 File "test.py", line 63
    if self.simplified_numerator == other.simplified_numerator and 
                                                                  ^
SyntaxError: invalid syntax
```I named it test.py...am I doing something wrong, or is this a valid error??
I am fairly certain that it is me...but I would really like to know what I am supposed to do.

---

### Post by mssever on 2008-02-29
I've updated my submission (post 27). Changes include a much superior GCD algorithm which I found on Wikipedia (my math skills are terrible) and proper type coersion so math operations can be seamlessly performed between Fraction, Integer, and Float.

---

### Post by rbprogrammer on 2008-02-29
> **Siph0n said:**
> 
Since everyone else is doing C++/C/Python... thought I would switch it up :) Here it is in Ada95
...

Ah lol Siph0n, I'm going to switch it up even more and use Scheme:
```

(define frac_create (lambda (u v) ( cons u ( cons v () ))))
(define frac_mult (lambda (u v x y) ( cons (+ u x) (cons (* v y) ())) ))
(define frac_print (lambda (u v) ((display u) (display "/") (display v))))

(define frac_recip (lambda (u v) (cons v (cons u ()))))
(define frac_add (lambda (u v x y) (cons (+ (* u y) (* v x)) (cons (*v y) ()))))
(define frac_sub (lambda (u v x y) (cons (- (* u y) (* v x)) (cons (*v y) ()))))
(define frac_div (lambda (u v x y) (frac_mult u v y x)))
(define frac_todecimal (lambda (u v) (/ u v)))
(define deci_tofraction (lambda (u) (display "not enough time to figure this one out :( ")))

```
I'm a bit rusty, but you get the gist of the language :guitar: .....

---

### Post by sryth on 2008-02-29
You can't use any fraction libraries already created - you must code them from scratch! A winner will be picked on Wednesday the fifth of March based on the above.


I guess this means no using languages that treat fractions as numbers without extra libraries. :)

---

### Post by amingv on 2008-03-01
Well, I have decided to ride the carousel with another of my C++ abominations. I must say that this one has a special meaning: it's teached me, for the first time, how to use a debugger (namely gdb). I think it does the basics fine and I'll continue to tweak it, but that'll be another time when it's not 3:20 in a Friday's evening/Saturday's morning :roll:.

Tests (main.cpp):
[PHP]#include <iostream>

#include "fraction.h"

int main(int argc, char* argv[]){
    
    std::cout.precision(3);

    Fraction one_half = 0.5;
    one_half.simplify();
    Fraction one_third (1000, 3000);
    one_third.simplify();
    Fraction one_fourth (1, 4);
    Fraction three_fourths = 0.75;
    three_fourths.simplify();
    //Test convert from zero or from negative
    Fraction one_fifth (0, -5);
    Fraction one_whole = 0;
    one_whole.simplify();
    //Test negative fractions
    Fraction minus_one_half = -0.5;
    minus_one_half.simplify();
    Fraction minus_one_third (-1, -3);
    
    std::cout<< "Here are the values:\n";
    one_half.print(); std::cout<<"\n";
    one_third.print(); std::cout<<"\n";
    one_fourth.print(); std::cout<<"\n";
    three_fourths.print(); std::cout<<"\n";
    one_fifth.print(); std::cout<<"\n";
    one_whole.print(); std::cout<<"\n";
    minus_one_half.print(); std::cout<<"\n";
    minus_one_third.print(); std::cout<<"\n";
    
    std::cout<< "\nAnd some operations:\n";
    std::cout<< "one_half + one_third = "; (one_half + one_third).print(); std::cout<<"\n";
    std::cout<< "one_half - minus_one_half = "; (one_half - minus_one_half).simplify().print(); std::cout<<"\n";
    std::cout<< "one_fifth * three_fourths = "; (one_fifth * three_fourths).print(); std::cout<<"\n";
    std::cout<< "three_fourths / one_half = "; (three_fourths / one_half).print(); std::cout<<"\n";
    
    std::cout<< "\nClass functions:\n";
    one_fifth.reciprocal().print(); std::cout<<"\n";
    three_fourths.reciprocal().print(); std::cout<<"\n";
    std::cout<< three_fourths.reciprocal().dbl() <<"\n";
    std::cout<< one_half.dbl() <<"\n";
    std::cout<< one_fifth.dbl() <<"\n";
    std::cout<< one_fourth.dbl() <<"\n";
    
    std::cout<< "\nTrue or false?\n";
    if (one_half == (Fraction(-1, 1)*minus_one_half)) std::cout<< "one_half == (-1*minus_one_half)\n";
    if (one_half < one_whole) std::cout<< "one_half < one_whole\n";
    if (one_half <= one_half) std::cout<< "one_half <= one_half\n";
    if (one_half > one_fourth) std::cout<< "one_half > one_fourth\n";
    if (one_half >= one_third) std::cout<< "one_half >= one_third\n";
    if (one_half != one_fifth) std::cout<< "one_half != one_fifth\n";

    return 0;
}
[/PHP]

Output:
```
$ ./main
Here are the values:
1/2
1/3
1/4
3/4
1/5
1/1
-1/2
-1/3

And some operations:
one_half + one_third = 5/6
one_half - minus_one_half = 1/1
one_fifth * three_fourths = 3/20
three_fourths / one_half = 6/4

Class functions:
5/1
4/3
1.33
0.5
0.2
0.25

True or false?
one_half == (-1*minus_one_half)
one_half < one_whole
one_half <= one_half
one_half > one_fourth
one_half >= one_third
one_half != one_fifth

```

fraction.h
[PHP]class Fraction {
    int num, denom;
    
public:
    //constructors
    Fraction();
    Fraction(int n, int d);
    Fraction(double n);
    
    //functions
    void print();
    double dbl() const;
    Fraction simplify();
    Fraction reciprocal() const;
    
    //mathematical operators
    Fraction operator+ (const Fraction &right);
    Fraction operator- (const Fraction &right);
    Fraction operator* (const Fraction &right);
    Fraction operator/ (const Fraction &right);
    
    //boolean/comparison operators
    bool operator== (const Fraction &right) const;
    bool operator< (const Fraction &right) const;
    bool operator> (const Fraction &right) const;
    bool operator<= (const Fraction &right) const;
    bool operator>= (const Fraction &right) const;
    bool operator!= (const Fraction &right) const;
};
[/PHP]

fraction.cpp
[PHP]#include <iostream>

#include "fraction.h"

//constructors
Fraction::Fraction() {}

Fraction::Fraction(int n, int d){
    /*Constructor criteria:
        1. If n or d == 0, then n or d defaults to one.
        2. If d is negative, then d defaults to the same number, but positive. (To allow a negative fraction -n/d)
    */
    if (n == 0) n = 1;
    if (d == 0) d = 1;
    if (d < 0) d = (d*-1);
    //assign verified data
    num = n;
    denom = d;
}

Fraction::Fraction(double n){
    /*Constructor criteria:
        1. If n == 0, then n defaults to one point zero.
        2. If n is negative, the result will be a negative fraction of kind -n/d.
    */
    if (n == 0) n = 1.0;
    //assign verified data
    num = int((n * 100));
    denom = 100;
}

//functions
void Fraction::print(){
    std::cout<< num <<'/' <<denom;
}

double Fraction::dbl() const{
    return (double(num)/double(denom));
}

Fraction Fraction::simplify(){
    int i;
    int pos_neg = 1;
    if (num < 0) pos_neg = -1;
    if (num <= denom) i = (num * pos_neg);
    else if (num < denom) i = denom;
    
    while (i > 0) {
        if (((num % i) == 0) && ((denom % i) == 0)) {
            num = (num/i);
            denom = (denom/i);
        }
        i--;
    }
    return Fraction((num * pos_neg), denom);
}

Fraction Fraction::reciprocal() const {
    int n, d;
    if (num < 0) {
        n = (num * -1);
        d = (denom * -1);
    }
    else {
        n = num;
        d= denom;
    }
    return Fraction(d, n);
}

//mathematical operators
Fraction Fraction::operator+ (const Fraction &right){
    if (denom == right.denom) {
        return Fraction((num + right.num), denom);
    }
    else {
        Fraction left_common  ((num * right.denom), (denom * right.denom));
        Fraction right_common ((right.num * denom), (right.denom * denom));
        return (left_common + right_common);
    }
}

Fraction Fraction::operator- (const Fraction &right){
    if (denom == right.denom) {
        return Fraction((num - right.num), denom);
    }
    else if ((denom == right.denom) && (num < right.num)) {
        return Fraction((right.num - num), denom);
    }
    else {
        Fraction left_common  ((num * right.denom), (denom * right.denom));
        Fraction right_common ((right.num * denom), (right.denom * denom));
        return (left_common + right_common);
    }
}

Fraction Fraction::operator* (const Fraction &right){
    return Fraction((num * right.num), (denom * right.denom));
}

Fraction Fraction::operator/ (const Fraction &right){
    return Fraction((num * right.reciprocal().num), (denom * right.reciprocal().denom));
}

//boolean/comparison operators
bool Fraction::operator== (const Fraction &right) const{
    return ((num == right.num) && (denom == right.denom));
}
//Compare doubles, since it's a much easier approach
bool Fraction::operator< (const Fraction &right) const{
    return (dbl() < right.dbl());
}

bool Fraction::operator> (const Fraction &right) const{
    return (dbl() > right.dbl());
}

bool Fraction::operator<= (const Fraction &right) const{
    return (dbl() <= right.dbl());
}

bool Fraction::operator>= (const Fraction &right) const{
    return (dbl() >= right.dbl());
}

bool Fraction::operator!= (const Fraction &right) const{
    return ((num != right.num) || (denom != right.denom));
}
[/PHP]

Although simplify() works well so far, I need to find a way to "embed" it so that any value is automatically simplified, this is specially necessary for the comparison operators:
```
(Fraction(1, 2) == Fraction(50, 100))
```
Would evaluate to false, but I haven't worked around that yet. (At least no without getting a segfault)#-o

---

### Post by DemonDomen on 2008-03-01
> **seventhc said:**
> I am sure it is me, something I am doing wrong...but I get an error when I run this...here is the error
```
 File "test.py", line 63
    if self.simplified_numerator == other.simplified_numerator and 
                                                                  ^
SyntaxError: invalid syntax
```I named it test.py...am I doing something wrong, or is this a valid error??
I am fairly certain that it is me...but I would really like to know what I am supposed to do.

Is that a newline after "and"? If it is, try to remove it and test it.

---

### Post by Martin Witte on 2008-03-01
> **seventhc said:**
> I am sure it is me, something I am doing wrong...but I get an error when I run this...here is the error
```
 File "test.py", line 63
    if self.simplified_numerator == other.simplified_numerator and 
                                                                  ^
SyntaxError: invalid syntax
```I named it test.py...am I doing something wrong, or is this a valid error??
I am fairly certain that it is me...but I would really like to know what I am supposed to do.

You have to add a backslash at the end, the command in the original file is on more lines - somehow the PHP formatter loses the ending backslash

---

### Post by seventhc on 2008-03-01
> **Martin Witte said:**
> You have to add a backslash at the end, the command in the original file is on more lines - somehow the PHP formatter loses the ending backslash
That did it, thanks :)

---

### Post by nick_h on 2008-03-04
Here is a solution that I've written in Java.  I think that it implements most of the features requested.  The only problem that I'm aware of at the moment is that generating an overflow does not throw an ArithmeticException as I expected.

[php]public class Fraction implements Comparable {
	
	public final static Fraction ZERO = new Fraction(0, 1);
	public final static Fraction ONE = new Fraction(1, 1);
	
	private final long num;
	private final long den;

	// Decimal to fraction approximation
	public static Fraction getFraction(double value) {
		double d, approx;
		long l;
		int i;
		long[] num = new long[20];
		long[] den = new long[20];
		
		num[0] = 0;
		num[1] = 1;
		den[0] = 1;
		den[1] = 0;
		d = value;
		
		for (i = 2; i < 20; i++)  {		
			l = (long)Math.floor(d);		    
		    num[i] = l * num[i-1] + num[i-2];
		    den[i] = l * den[i-1] + den[i-2];

		    approx = (double)num[i] / den[i];
		    if (approx == value) break;
		    
		    d = 1 / (d - l);
		}		
		return new Fraction(num[i], den[i]);
	}
	
	// Functions for gcd and lcm
	public static long gcd(long a, long b) {
		if (b == 0)
			return a;
		else
			return gcd(b, a % b);
	}
    
	public static long lcm(long a, long b) {
		return (a / gcd(a, b)) * b;
	}
	
	//  Constructors
	public Fraction(long n, long d) {
		long divisor;
		if (d == 0) 
			throw new IllegalArgumentException("Denominator cannot be zero.");
		if (n ==0)
			d = 1;
		if (d < 0) {
			d = -d;
			n = -n;
		}
		divisor = gcd(Math.abs(n), d);
		this.num = n / divisor;
		this.den = d / divisor;
	}
	
	public Fraction(long n) {
		this(n, 1);
	}

	// Type conversions
	public String toString() {
		if (this.den == 1) {
			return "" + this.num;
		} else {
			return this.num + "/" + this.den;
		}
	}
	
	public String toMixedString() {
		long i, f;
		String s;
		
		if (this.den == 1) {
				s = "" + this.num;
		} else {
			i = this.num / this.den;
			if (i != 0) {
				f = Math.abs(this.num % this.den);
				s = i + " " + f + "/" + this.den;
			} else {
				s = this.num + "/" + this.den;
			}
		}
		return s;
	}
	
	public double toDouble() {
		return (double)this.num / this.den;
	}
	
	// Arithmetic
	public Fraction add(Fraction a) {
		long n, d;
		d = lcm(a.den, this.den);
		n = (d / a.den) * a.num + (d / this.den) * this.num;
		return new Fraction(n, d);
	}
	
	public Fraction multiply(Fraction a) {
			long n, d;
			n = a.num * this.num;
			d = a.den * this.den;
			return new Fraction(n, d);
	}

	public Fraction negate() {
		return new Fraction(-this.num, this.den);
	}
	
	public Fraction reciprocal() {
		if (this.num == 0) 
			throw new ArithmeticException("Divide by zero.");
		return new Fraction(this.den, this.num);
	}
	
	public Fraction subtract(Fraction a) {
		return this.add(a.negate());
	}
	
	public Fraction divide(Fraction a) {
		return this.multiply(a.reciprocal());
	}

	// Comparisons
	public int compareTo(Object o) {		
		Fraction diff = this.subtract((Fraction) o);
		if (diff.num == 0)
			return 0;
		else if (diff.num > 0)
			return 1;
		else
			return -1;
	}
	
	public boolean equals(Object o) {	
		if (!(o instanceof Fraction))
		    return false;
		
		Fraction f = (Fraction) o;
		if ((f.num == this.num) & (f.den == this.den))
			return true;
		else
			return false;
	}
	
	// Testing
	public static void main(String[] args) {

		Fraction f1, f2, f3, f4, f5, f6;
		
		System.out.println("Arithmetic tests");
		f1 = new Fraction(1 ,2);
		f2 = new Fraction(3, 7);
		System.out.println("f1 = " + f1);
		System.out.println("f2 = " + f2);
		System.out.println("f1 + f2 = " + f1.add(f2));
		System.out.println("f1 - f2 = " + f1.subtract(f2));
		System.out.println("f1 * f2 = " + f1.multiply(f2));
		System.out.println("f1 / f2 = " + f1.divide(f2));
		System.out.println("-f1 / f2 = " + f1.negate());
		System.out.println("1/f2 = " + f2.reciprocal());
		
		System.out.println("Comparison tests");
		if (f1.compareTo(f2) == 1)
			System.out.println("f1 > f2");
		if (f2.compareTo(f1) == -1)
			System.out.println("f1 < f2");
		if (f1.compareTo(f1) == 0)
			System.out.println("f1 = f2");
		if (f1.equals(f1))
			System.out.println("f1 = f2");
		if (!f1.equals(f2))
			System.out.println("f1 != f2");
		
		System.out.println("Conversion tests");
		f3 = new Fraction(33, -13);
		System.out.println("f3 = " + f3);
		System.out.println("Mixed format f3 = " + f3.toMixedString());
		System.out.println("f3 as double = " + f3.toDouble());

		System.out.println("Approximation of double tests");
		f4 = Fraction.getFraction(Math.PI);
		System.out.println("PI = " + f4);
		System.out.println("PI = " + f4.toDouble());
		System.out.println("Error = " + (f4.toDouble() - Math.PI));
		
		System.out.println("Exception tests");
		f5 = new Fraction(0,4);
		try {
			System.out.println(f5.reciprocal());
		} catch (ArithmeticException e) {
			System.out.println(e.getMessage());
		}
		try {
			f5 = new Fraction(4,0);
		} catch (IllegalArgumentException e) {
			System.out.println(e.getMessage());
		}
		try {
			f6 = new Fraction(1,10000000000L);
			System.out.println("1/10G + 1/10G = " + f6.add(f6));
			System.out.println("1/10G * 1/10G = " + f6.multiply(f6));
		} catch (ArithmeticException e) {
			System.out.println(e.getMessage());
		}
		
		System.out.println("Zero and One tests");
		System.out.println("f2 + 0 = " + f2.add(Fraction.ZERO));
		System.out.println("f2 * 0 = " + f2.multiply(Fraction.ZERO));
		System.out.println("f2 + 1 = " + f2.add(Fraction.ONE));
		System.out.println("f2 * 1 = " + f2.multiply(Fraction.ONE));
		
	}

}
[/php]

---

### Post by Lster on 2008-03-04
Have your entries in as soon as possible for the judging! I'll post tomorrow when I wake up with the winner... and then they can create the next challenge! :)

---

### Post by qix on 2008-03-04
I'm really new at C programming, so I learned from this :) Here is my naive approach. I know I'm not gonna win, but I'd really like feedback if there can be improvements to my code!

It's written in C.

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

struct frc {
	int numerator;
	int denominator;
};

struct frc * new_fraction(int, int);
void print_fraction(struct frc *);
void reduce_fraction (struct frc *);
struct frc multiply_fraction(struct frc *, struct frc *);
struct frc add_fraction(struct frc *, struct frc *);
struct frc subtract_fraction(struct frc *, struct frc *);
struct frc invert_fraction(struct frc *);
double frac2decimal (struct frc * f);

int main(int argv, char ** argc) {
	struct frc * f1;
	struct frc * f2;
	f1 = new_fraction(2,3);
	f2 = new_fraction(2,-4);

	struct frc * f3;
	f3 = new_fraction(0,1);
	
	*f3 = add_fraction(f1,f2);
	print_fraction(f3);

	*f3 = subtract_fraction(f1,f2);
	print_fraction(f3);

	*f3 = multiply_fraction(f1,f2);
	print_fraction(f3);

	printf("%f\n",frac2decimal(f3));

	*f3 = invert_fraction(f3);
	print_fraction(f3);

	
	free(f1);
	free(f2);
	free(f3);
	return 0;
}

struct frc * new_fraction (int n, int d) {
	struct frc * f = malloc(sizeof(struct frc));
	if (d == 0) {
		printf("Denominator cannot be 0, setting it to 1.\n");	
		d = 1;
	}

	(*f).numerator = n;
	(*f).denominator = d;
	return f;
}

void print_fraction (struct frc * f) {
	/* Mixed-mode output is ambiguous, and as a mathematician, I don't approve of it */

	if ((*f).numerator * (*f).denominator < 0)
		 printf("-");

	abs((*f).denominator) == 1 ? printf("%d\n",abs((*f).numerator)) : printf("%d/%d\n",abs((*f).numerator),abs((*f).denominator));
}

void reduce_fraction (struct frc * f) {
	/* Euclidean algorithm */
	int a = (*f).numerator;
	int b = (*f).denominator;
	int t;
	while (b != 0) {
		t = b;
		b = fmod(a,b);
		a = t;
	}
	(*f).numerator /= a;
	(*f).denominator /= a;
}

struct frc multiply_fraction (struct frc * f1, struct frc * f2) {
	struct frc f3;
	f3.numerator = (*f1).numerator * (*f2).numerator;
	f3.denominator = (*f1).denominator * (*f2).denominator;
	reduce_fraction(&f3);
	return f3;
}

struct frc add_fraction (struct frc * f1, struct frc * f2) {
	struct frc f3;
	f3.numerator = (*f2).denominator * (*f1).numerator + (*f1).denominator * (*f2).numerator;
	f3.denominator = (*f1).denominator * (*f2).denominator;
	reduce_fraction(&f3);
	return f3;
}

struct frc subtract_fraction (struct frc * f1, struct frc * f2) {
	struct frc f3;
	f3.numerator = (*f2).denominator * (*f1).numerator - (*f1).denominator * (*f2).numerator;
	f3.denominator = (*f1).denominator * (*f2).denominator;
	reduce_fraction(&f3);
	return f3;
}

struct frc invert_fraction (struct frc * f1) {
	struct frc f2;
	f2.numerator = (*f1).denominator;
	f2.denominator = (*f1).numerator;
	reduce_fraction(&f2);
	return f2;
}

double frac2decimal (struct frc * f) {
	double decimal;
	decimal = (double) (*f).numerator / (*f).denominator;
	return decimal;
}
```

It gives me the simple output:
```
kristian@kristianlap:~/c$ gcc -lm -Wall fraction.c 
kristian@kristianlap:~/c$ ./a.out 
1/6
7/6
-1/3
-0.333333
-3
```

---

### Post by guitsaru on 2008-03-04
Here's my submission, in Ruby.

```

class Fraction
  attr_reader :numerator, :denominator
  
  def initialize(numerator, denominator)
    @numerator = numerator
    @denominator = denominator
  end
  
  def print
    @numerator.to_s + "/" + @denominator.to_s
  end
  
  def reciprocal
    Fraction.new(@denominator, @numerator).simplify
  end
  
  def gcd(a, b)
    b <=> a if b > a
    return a if b ==0
    gcd(b, a % b)
  end
  
  def simplify
    gcf = gcd(@numerator, @denominator)
    Fraction.new(@numerator/gcf, @denominator/gcf)
  end
  
  def *(other)
    Fraction.new(@numerator*other.numerator,
      @denominator*other.denominator).simplify
  end
  
  def /(other)
    Fraction.new(@numerator*other.denominator,
      @denominator*other.numerator).simplify
  end
  
  def +(other)
    fraction1 = Fraction.new(@numerator*other.denominator,
      @denominator*other.denominator)
    fraction2 =  Fraction.new(@denominator*other.numerator,
      @denominator*other.denominator)
    Fraction.new(fraction1.numerator+fraction2.numerator,
      fraction1.denominator).simplify
  end
  
  def -(other)
    fraction1 = Fraction.new(@numerator*other.denominator,
      @denominator*other.denominator)
    fraction2 =  Fraction.new(@denominator*other.numerator,
      @denominator*other.denominator)
    Fraction.new(fraction1.numerator-fraction2.numerator,
      fraction1.denominator).simplify
  end
  
  def ==(other)
    f1 = simplify
    f2 = other.simplify
    
    if f1.numerator == f2.numerator && f1.denominator == f2.denominator
      return true
    end
    return false
  end
  
  def value
    decimal = Float(@numerator) / Float(@denominator)
  end
end

class Float
  def to_fraction
    digits = self.to_s.gsub(/.*\./, "").length
    Fraction.new(self*(10**digits), 10**digits).simplify
  end
end

```

And, just for fun, my unit tests:
```

require "test/unit"

require "fraction"

class TestFraction < Test::Unit::TestCase
  def setup
    @fraction = Fraction.new(2,3)
    @unsimplified = Fraction.new(6,9)
    @unsimplified2 = Fraction.new(1800, 18)
  end
  def test_initialize
    assert_equal(Fraction.new(2,3), @fraction)
  end
  def test_multiplication
    test_fraction = @fraction * @fraction
    assert_equal(Fraction.new(4,9), test_fraction)
  end
  def test_print
    assert_equal("2/3", @fraction.print)
  end
  def test_reciprocal
    test_fraction = Fraction.new(3,2)
    assert_equal(test_fraction, @fraction.reciprocal)
  end
  def test_gcd
    assert_equal(2, @fraction.gcd(206, 40))
    assert_equal(2, @fraction.gcd(40, 206))
  end
  def test_simplify
    assert_equal(@fraction, @unsimplified.simplify)
    assert_equal(Fraction.new(100,1), @unsimplified2.simplify)
  end
  def test_add
    test_fraction = @fraction + @unsimplified
    assert_equal(Fraction.new(4,3), test_fraction)
  end
  def test_subtract
    test_fraction = @fraction - Fraction.new(3, 9)
    assert_equal(Fraction.new(1,3), test_fraction)
  end
  def test_divide
    test_fraction = Fraction.new(1,2) / Fraction.new(1,4)
    assert_equal(Fraction.new(2,1), test_fraction)
  end
  def test_equal
    assert_equal(@fraction, @unsimplified)
  end
  def test_value
    assert_equal(0.25, Fraction.new(1,4).value)
  end
  def test_float_to_fraction
    assert_equal(Fraction.new(1,4), 0.25.to_fraction)
  end
end

```

---

### Post by Lster on 2008-03-05
Well it's time to judge and the winner is...

aks44

His solution was very well commented, neat and most impressively had a very effective FromDouble function. He is now responsible for creating the next challenge. I look forwards to participating! :)

---

### Post by compwiz18 on 2008-03-05
I realize I'm a little late to the party, but since I've got something, I'm gonna post it anyway :KS

In Python:
```
# The Fraction Class
# Can add, subtract, and multiply fractions, as well as simplify them.
# Copyright 2008 Adam Blackburn

# NOTES:
# When I say a function accepts nothing,
# this does not mean that it does not accept
# self as the first argument.

class Fraction:
    def __init__(self, num, den):
        '''
        Accepts:
                A numerator and a denominator.
                
        Returns:
                Nothing.
                
        Creates a new Fraction.
        '''
        self.num = num
        self.den = den
        
    def __str__(self):
        '''
        Accepts:
                Nothing.
                
        Returns:
                A string representation of self.
        '''
        self.__simplify_fraction()
        if self.den != 1:
            return str(self.num) + "/" + str(self.den)
        else:
            return str(self.num)
        
    def __add__(self, other):
        '''
        Accepts:
                One fraction.
                
        Returns:
                A fraction that is the result of adding the two recieved fractions.
        '''
        frac1, frac2 = self.__prepare_for_addition_subtraction(other)

        new_num = frac1.num + frac2.num
        
        return (Fraction(new_num, frac1.den))
        
    def __sub__(self, other):
        '''
        Accepts:
                One fraction.
                
        Returns:
                A fraction that is the result of subtracting the two recieved fractions.
        '''
        frac1, frac2 = self.__prepare_for_addition_subtraction(other)

        new_num = frac1.num - frac2.num
        
        return (Fraction(new_num, frac1.den)) # doesn't matter which denominator is used; they are both the same
        
    def __mul__(self, other):
        '''
        Accepts:
                One fraction.
                
        Returns:
                A fraction that is the result of multiplying the two recieved fractions.
        '''
        new_num = self.num * other.num
        new_den = self.den * other.den
        
        return Fraction(new_num, new_den)
        
    def __prepare_for_addition_subtraction(self, other):
        '''
        Accepts:
                One fraction.
                
        Returns:
                Two fractions (in a tuple) with the same denominator.
        ''' 
        my_new_num = self.num * other.den
        other_new_num = other.num * self.den
        new_dem = self.__find_common_denominator(other)
                
        return (Fraction(my_new_num, new_dem), Fraction(other_new_num, new_dem))

    def __find_common_denominator(self, other):
        '''
        Accepts:
                One fraction.
                
        Returns:
                The common denominator of the two fractions.
        '''
        return self.den * other.den
        
    def __simplify_fraction(self):
        '''
        Accepts:
                Nothing.
                
        Returns:
                Nothing.
                
        Computes the simplified version of self.
        '''
        i = 1
        while (i <= (max(self.num, self.den) / 2)):
            if self.num % i == 0 and self.den % i == 0:
                self.num = self.num / i
                self.den = self.den / i
                i = 1
                
            i += 1
        

x = Fraction(5,2)
y = Fraction(4,2)

print "x: " + str(x)
print "y: " + str(y)
print "x + y: " + str(x + y)
print "x - y: " + str(x - y)
print "x * y: " + str(x * y)
```

Output:
```
$ python fractions.py                                                                        (03-05 06:57)
x: 5/2
y: 2
x + y: 9/2
x - y: 1/2
x * y: 5

```

Feedback is welcome :D

---

### Post by Siph0n on 2008-03-05
You wake up too early Lster.... lol I was gonna add some things to my program this morning :) Added Addition, Division, Subtraction, and Simplification to my Ada95 post if anyone cares to see....

---

### Post by Lster on 2008-03-05
Well it's 10 to one here, now. I was up quite later really! :)

---

### Post by pedro_orange on 2008-03-05
Congrats Aks44, I eagrely await your challenge

---

### Post by Lux Perpetua on 2008-03-05
Congratulations, aks44! 

When I referred to a possible second submission, I was thinking of this: [http://www.cs.ru.nl/~milad/publications/JDA_04_06.pdf](http://www.cs.ru.nl/~milad/publications/JDA_04_06.pdf)

That representation of rational numbers is probably alien to most of you. A positive fraction is represented in a very natural way by a binary string (which has nothing to do with integers in base 2). If you run with the idea of continued fractions to the extreme, this is what you might end up with. 

I decided against it after reading the algorithms in that paper, which  do require ordinary arithmetic on integers; they don't work purely in the "SB" representation, in the author's notation. Maybe I'm unfair, but that feels like cheating. :-P

---

### Post by aks44 on 2008-03-05
Thanks for that. :D


I'm currently working on the next challenge, expect it soon... ;)

---

### Post by Lster on 2008-03-05
[QUOTE=aks44]I'm currently working on the next challenge, expect it soon...[/QUOTE]

Muahaha! Looking forward to it! :)

---

### Post by Martin Witte on 2008-03-05
Congratulations ask44!

---

### Post by WitchCraft on 2009-01-10
Programming **"challenge"**?

I did that in the 3rd or 4th class of primary school, with Turbo Pascal for (DR-)DOS...

I hardly see a challenge in this...

---

### Post by seventhc on 2009-01-10
> **WitchCraft said:**
> Programming **"challenge"**?

I did that in the 3rd or 4th class of primary school, with Turbo Pascal for (DR-)DOS...

I hardly see a challenge in this...
Then don't play.

---

### Post by mike_g on 2009-01-10
Lol, yeah not much of a reason to resurrect a year old thread over.

---

