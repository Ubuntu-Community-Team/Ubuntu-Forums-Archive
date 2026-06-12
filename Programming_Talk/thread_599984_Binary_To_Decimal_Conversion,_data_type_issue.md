---
title: "Binary To Decimal Conversion, data type issue"
date: 2007-11-01
forum: Programming Talk
---

### Post by jpittack on 2007-11-01
I am new to C++ and I can not figure out how to fix these compile errors.  I must use a function.

The errors

> [jpittack@vulcan ~]$ g++ -Wall program14.cpp
program14.cpp: In function `double bincovert(double)':
program14.cpp:49: error: integer constant is too large for "long" type
program14.cpp:52: warning: unused variable 'a'
program14.cpp:54: warning: unused variable 'a'
program14.cpp:56: error: invalid operands of types `double' and `double' to binary `operator%'
program14.cpp:59: warning: unused variable 'b'
program14.cpp:61: warning: unused variable 'b'
program14.cpp:63: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:66: warning: unused variable 'c'
program14.cpp:68: warning: unused variable 'c'
program14.cpp:70: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:73: warning: unused variable 'd'
program14.cpp:75: warning: unused variable 'd'
program14.cpp:77: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:80: warning: unused variable 'e'
program14.cpp:82: warning: unused variable 'e'
program14.cpp:84: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:87: warning: unused variable 'f'
program14.cpp:89: warning: unused variable 'f'
program14.cpp:91: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:94: warning: unused variable 'g'
program14.cpp:96: warning: unused variable 'g'
program14.cpp:98: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:101: warning: unused variable 'h'
program14.cpp:103: warning: unused variable 'h'
program14.cpp:105: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:108: warning: unused variable 'i'
program14.cpp:110: warning: unused variable 'i'
program14.cpp:112: error: invalid operands of types `double' and `int' to binary `operator%'
program14.cpp:115: warning: unused variable 'j'
program14.cpp:117: warning: unused variable 'j'
[jpittack@vulcan ~]$

The program

> #include <iostream>
using namespace std;

double binconvert (double number )

int main ()
{
double number;
cout << "Enter a binary number to convert to decimal format" << endl;
cin >> number;
cout << binconvert (number) << ":" << number << endl;
return 0;
}

double bincovert ( double  number)

{
double rem = 0;
int a = 0;
int b = 0;
int c = 0;
int d = 0;
int e = 0;
int f = 0;
int g = 0;
int h = 0;
int i = 0;
int j = 0;
double z = 10000000000;

  if ( number / z == 1 )
   int a = 512;
  if ( number / z != 1 )
   int a = 0;

  rem =  number % z;

  if ( rem /  1000000000 == 1 )
   int b = 256;
  if ( rem /  1000000000 != 1 )
   int b = 0;

  rem = rem %  1000000000;

  if ( rem / 100000000 == 1 )
   int c = 128;
  if ( rem / 100000000 != 1 )
   int c = 0;

  rem = rem % 100000000;

  if ( rem / 10000000 == 1)
   int d = 64;
  if ( rem / 10000000 != 1)
   int d = 0;

  rem = rem % 10000000;                                                                                                                                           34,0-1        42%

  if ( rem / 1000000 == 1)
   int e = 32;
  if ( rem / 1000000 != 1)
   int e = 0;

  rem = rem % 1000000;

  if ( rem / 10000 == 1)
   int f = 16;
  if ( rem / 10000 != 1)
   int f = 0;

  rem = rem % 10000;

  if ( rem / 1000 == 1)
   int g = 8;
  if ( rem / 1000!= 1)
   int g = 0;

  rem = rem % 1000;

  if ( rem / 100 == 1)
   int h = 4;
  if ( rem / 100 != 1)
   int h = 0;

  rem = rem % 100;

  if ( rem / 10 == 1)
   int i = 2;
  if ( rem / 10  != 1)
   int i = 4;

  rem = rem % 10;

  if ( rem / 1 == 1)
   int j = 1;
  if ( rem / 1 != 1)
   int j = 0;

number = a + b + c + d + e + f + g + h + i + j;

return number;
}


Thanks!

---

### Post by YetAnotherNoob on 2007-11-01
> **jpittack said:**
> 
int main ()
{
double number;
cout << "Enter a binary number to convert to decimal format" << endl;
cin >> number;
cout << binconvert (nmber**)** << ":" << number << endl;
return 0;
}


syntax error.
u need to close the paranthesis to the function call binconvert.

---

### Post by jpittack on 2007-11-01
I am using Putty, and I was copying parts of the program as they did not copy from the clipboard.  This mistake does not exist in the program itself.

Sorry.

---

### Post by CptPicard on 2007-11-01
... and your forward declaration of 

```

double binconvert (double number )

```

is missing a semicolon at the end... can't remember if you needed to forward declare in C++ like that...

Why are you reading your input into a double? Why not a string of 0s and 1s which you could then parse? Your code looks horribly contrived and complicated, the correct function is essentially one loop and a few variables...

EDIT: Ok, here goes a more complete explanation of what you need to be doing. I'm not doing your homework for you but the general idea.. sorry I can't be bothered to debug your actual code ;)

First, read your input as a string. A C++ string or char[], doesn't matter.

In the function, get a result variable, say int x, and initialize to zero.

Iterate from left to right over your input string. At each step, check if position is 1. If so, add 1. If not, do nothing. Shift x to the left by one bit by "x = x << 1". Loop until done with string. Return x and print it.

I'm not sure if you're allowed to use the bit shift, in case you have to go the hard way and, say, iterate your string from the least-significant bit to the most-significant bit and do the 2^i addition thing to your result. In this case you need to know your string length, which you may have to check in advance.

---

### Post by Paul820 on 2007-11-01
You can't use the modulo operator '%' on doubles, it can only be used on integers.

---

### Post by jpittack on 2007-11-01
How do I solve the problem of the 

program14.cpp:49: error: integer constant is too large for "long" type

This is why I tried doubles.

I can't use string.  Beyond the capabilities that I am allowed to use.

Why do I need a loop?

---

### Post by jpittack on 2007-11-01
In addition, I am supposed to be using code from my decimal to binary conversion program.

The number is only 10 digits long.

Must have a function.

Follows this format, which I will revert my code to.

int main ()
{
int foo;
cout << "enter a binary number and I will convert it for you: " << flush;
cin >> foo;
cout << bincovert (foo) << ":" << foo << endl;
return 0
}

//put code for function binconvert() right here

---

### Post by CptPicard on 2007-11-01
Ah, sorry, I misinterpreted your exercise... you're supposed to interpret the int as base2.

Could you tell me which line this offending line 49 exactly is, as in my editor it's an empty line... hard to tell. Your constants should fit into long... and you should start by replacing all of your doubles with longs, and probably ints too. Using double is just wrong and you should start by minimizing all the other bugs first.

As to why a loop... well.. it's just more compact and stylish.. :)

---

### Post by jpittack on 2007-11-01
I have what is called an Honor pledge preciding the actual code, which I left out. The line is...

int z=10000000000

which is 10,000,000,000

my errors have since changed to this problem and unused variable a,b,c,d,e,f,g,h,i,j

My procrastiontion means that this is due in 3 hours, so I don't want to bother with the loop, yet.  After we have a working program from this, perhaps you could explain the loop to me?  I am addicted to learning.  This is the main reason for having Ubuntu.

---

### Post by Paul820 on 2007-11-01
Also in your binconvert function you have declared all your variables from a to j but then you assign values to new ones:
```

if ( rem / 1000000000 == 1 )
int b = 256; <-- here, take out the 'int' and just leave b = 256; and the same for the rest
if ( rem / 1000000000 != 1 )
int b = 0; <-- here and all the way down for the others
```

---

### Post by jpittack on 2007-11-01
This solved one problem, now for this constant deal.  The last hurdle.

You guys are awesome.  Mabye next time I won't wait until the due date to start.  Thanks so much!

---

### Post by Paul820 on 2007-11-01
What constant?

---

### Post by jpittack on 2007-11-01
program14.cpp:49: error: integer constant is too large for "long" type

int z = 10000000000

I have tried long long int z = 10000000000

---

### Post by Paul820 on 2007-11-01
Try an **unsigned long z = 10000000000**

---

### Post by jpittack on 2007-11-01
same problem

---

### Post by Paul820 on 2007-11-01
Post what you have so far so we can get a better look at what we are dealing with. Don't forget to use the code tags though, highlight the code and click the # above where you type the message. :)

---

### Post by jpittack on 2007-11-01
Lost.  code tags? #?

At the moment I am in Vista, running putty to conect to a UNIX computer at school to type this code up.  I have no idea how to get the text from inside the putty window to anywhere else.

I can right click on the top border and copy to clipboard, but that does not always work.  I get code fragements.  I will try this unless you have a better idea.

---

### Post by Paul820 on 2007-11-01
Sorry for the confusion, i will have a look at your original code and see where it's going wrong. The code tags i mean are in the image, you just highlight the code and then click the # :)

---

### Post by CptPicard on 2007-11-01
Got it. :)

Use this for your long integer:

```

	unsigned long long z =  10000000000LLU;

```

You need to specifically declare your constant to be an unsigned long long by the suffix, because otherwise it will be a plain "int" constant, where of course your value does not fit. Also your datatype ought to be unsigned long long.

---

### Post by jpittack on 2007-11-01
On second thought, I am just going to switch to Ubuntu.  Putty is really slow under vista and I can't stand it.

---

### Post by YetAnotherNoob on 2007-11-01
If you want to use doubles you can 
#include <math.h>

and use function: fmod()

eg:
rem = fmod(number, z);

it does modulus for floating point numbers.

---

### Post by jpittack on 2007-11-01
That worked!

I think I was not doing this the way my instructer wanted me to, which is why I had no idea what the heck I was doing.

But thanks for all of the help!  Have some popcorn on me! :popcorn:

I don't have any more time tonight for the loop explanation, but I could learn about it tomorrow.  Until then, Cheers!

EDIT: Should have specifed what worked.  Just changing the int z to long long int z = 10000000LLU

---

### Post by Paul820 on 2007-11-01
> **CptPicard said:**
> Got it. :)

Use this for your long integer:

```

	unsigned long long z =  10000000000LLU;

```

You need to specifically declare your constant to be an unsigned long long by the suffix, because otherwise it will be a plain "int" constant, where of course your value does not fit. Also your datatype ought to be unsigned long long.

=D> Well done :)

---

### Post by CptPicard on 2007-11-01
> **jpittack said:**
> 
I think I was not doing this the way my instructer wanted me to, which is why I had no idea what the heck I was doing.

I suspect this as well, because this is not something that should be tripping up a homework assignment at this level.

> 
I don't have any more time tonight for the loop explanation, but I could learn about it tomorrow.  Until then, Cheers!

Prettifying that code as a further exercise would be preferable, yes. Frankly it makes my eyes hurt ;) Think about it, and ask if you need help with it...

---

### Post by the_unforgiven on 2007-11-03
I don't know what sort of experience/expertise the OP has, but AFAIUC doing it via divide-mod is quite not the optimized way.

Why not just look at bits of the number and determine what's the binary value?
This is basic binary arithmetic.

For example, to convert from binary to decimal, I would just do something like:
```

i = 0
decimal = 0

while i is less than or equal to the number of bits in the number
do
        extract the bit at the LSB in the number
        decimal <= decimal + (bit * (2^i))
        right shift the number by 1 bit.
        increment i - the counter.
done
```
HTH ;)

---

### Post by CptPicard on 2007-11-03
Actually this is essentially what I told him to do, with the exception that I was iterating from most significant bit and shifting the result. This has the added benefit that in particular if your bit string is of unknown length, you can just terminate when it ends, whenever it happens. Also, computing 2^i explicitly is slow, although it doesn't matter in this case probably.

Hopefully the OP is around to read the "proper solution" if some teaching assistant/professor hasn't enlightened him already :)

---

### Post by the_unforgiven on 2007-11-03
> **CptPicard said:**
> Also, computing 2^i explicitly is slow, although it doesn't matter in this case probably.

You could simply use (1 << i) to come to (2^i) - which I don't think is slow at all.

When I wrote that, I didn't mean to calculate (2^i) by explicit multiplication - if you were to use explicit multiplication, you lose out on the not using div-mod approach anyway.

Anyway, I hope that the OP has gotten some understanding of binary numbers by now :)
The whole point of such exercises is to understand the relation between binary and decimal (or any other) number system.

---

### Post by jpittack on 2007-11-04
My experience in programming is limited to this class, half way through the semester of it.  I am somewhat following what you are writting, but I have never used string, nor was I allowed to.  We can only use what knowledge he has taught us in class, so up to a certian chapter and section of the book.

Here is how the book explains converting.

Say the binary number is 101.  Working from right to left, you see if the digit is 1 or 0.  Take the 1 or 0, mulitple by its positional value, (1, 2, 4,8,16) and add the numbers that result to give you your decimal number.  Thus 1*1 + 0*2 + 1*4 = 5.

This is what I used.  Further resctricting me is that I must reuse old code, from about two weeks ago.  It was my decimal to binary program.  Thats why I had to divide.

---

### Post by CptPicard on 2007-11-04
Yeah, thought so. That's of course the "mathematical way" of doing things. And of course I hope you are aware that those magical multiplier numbers 1, 2, 4, 16 etc are powers of two -- 2^i, with i being position, counting from 0.

Also, that idea of interpreting a decimal representation of an int as binary is a bit unconventional, but for most of the discussion in this thread, it does not really matter where the information if whether the digit of interest is 1 or 0 comes from. Could be an int, could be a string... as long as we know which one it is at some position.

Now, as soon as we know *that* somehow, we can get to the point of constructing our result. The thing that probably confuses you is the bit shift operation... when you've got a binary number, shifting it left is equivalent to multiplication by two, whereas shifting right is equivalent to division by two, and discarding remainder. "Shifting" just moves digits left or right, and if you move left, adds zero as least significant digit, and if you move right, it removes the rightmost, least significant digit. In decimal you can multiply similarly by the base, 10, by adding a zero, or just removing the last digit.

Considering that your result variable int is stored inside the computer in binary anyway regardless of its (usual) decimal representation if you print it from your code, the easy way to copy the bit information from whatever source into your result is to just simply start with result = 0, adding a bit into that number, shifting result left by one position (thus making more room at the end of the number) and moving onto the next bit. :)

Soo... if you've got binary number 10101, say, and an 8-bit byte inited to 0:

```

Result: 00000000

Our bits:

10101
^--- bit of interest is 1, add 1 to result (or do an OR, but I'm not going to that here)

Result: 00000001

Shift result left:

Result: 00000010


10101
 ^--- bit of interest is 0, do nothing, just shift result

Result: 00000100

10101
  ^--- bit of interest is 1, add and shift

Result: 00001010

... and so on, you get the idea :)


```

---

### Post by jpittack on 2007-11-05
I supposed I get the idea.  I just don't know how to do it.  Because it is 6 at night and I have been up since 2:30 this morning, I don't think I will be bothering with this anytime soon.  I do go to class tomorrow, and I will be bringing this up.  Talk to you guys after that.

---

### Post by Sporkman on 2007-11-06
int result[MAX_WIDTH];

for ( i=0; i<MAX_WIDTH; ++i )
{
   result[i] = ( number & (1<<i) ) ? 1 : 0;
}

---

