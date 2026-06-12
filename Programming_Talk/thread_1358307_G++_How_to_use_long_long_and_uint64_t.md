---
title: "G++ How to use long long and uint64_t?"
date: 2009-12-18
forum: Programming Talk
---

### Post by OVERPOWER8 on 2009-12-18
Hello.

I need to write a program, that uses very long numbers, like                            923372036854775807.

But when I do it, I get an error:

```

#include <iostream>
#include <inttypes.h>

int main()
{
    uint64_t var1;
    long long var2;
    
    var1 = 923372036854775807;        // 11
    var2 = 923372036854775807;        // 12
}


```

**G++**

[I]_.cpp:11: error: integer constant is too large for &#8216;long&#8217; type
_.cpp:12: error: integer constant is too large for &#8216;long&#8217; type

[/I]Is there a way so I can work with such numbers?


[COLOR=Red]**NB! [COLOR=Black]numbers must be _integer_[/COLOR]**[/COLOR], no double, no float, no other types.

---

### Post by MadCow108 on 2009-12-18
put an LL or LLU behind:
var1 = 923372036854775807LLU;

---

### Post by OVERPOWER8 on 2009-12-18
> **MadCow108 said:**
> put an LL or LLU behind:
var1 = 923372036854775807LLU;

Thanks, but that's only long long.


I need to use also uint64_t with much greater numbers.
How can I do this?

---

### Post by Zugzwang on 2009-12-18
> **OVERPOWER8 said:**
> Thanks, but that's only long long.


I need to use also uint64_t with much greater numbers.
How can I do this?

Erm, wait. "long long" is usually 64bit in gcc, isn't it? I'm afraid that a "uint64_t" cannot store numbers more than twice as large (+1) as the one given.

```

#include <iostream>

int main() {
    std::cout << "#Bytes in long long: " << sizeof(long long) << "\n";
}

```
Running on a 32-bit machine: "#Bytes in long long: 8"
Running on a 64-bit machine: "#Bytes in long long: 8"

So an unsigned long long is equivalent to "uint64_t" on 32-bit and 64-bit machines using the GCC compiler.

---

### Post by Habbit on 2009-12-18
Using the C99 include file <stdint.h>, which will also be part of the next C++ standard as <cstdint>, you can use the standard integer constant macros, which transform the integer constant into the appropriate format for the type by appending the required suffixes. For example:```
#include <cstdint>

int main() {
    uint64_t n = UINT64_C(18446744073709551615);
    int64_t  m =  INT64_C(0x8000000000000000);
    return 0;
}
```

The [u]intN_t types and its associated macros translate into different things depending on the architecture. For example, on my 32bit Windows box, a 64-bit integer is an "[unsigned] long long", and thus the suffix appended is [u]LL, but in my 64-bit Ubuntu box it is a normal "[unsigned] long", so the suffix is simply [u]L.

---

### Post by dwhitney67 on 2009-12-18
The following code, which hopefully its intent is obvious:
```

#include <numeric>
#include <iostream>

int main()
{
   std::cout << std::numeric_limits<uint64_t>::max() << std::endl;
   std::cout << std::numeric_limits<int64_t>::max()  << std::endl;
}

```
produces the following output, which is the max numbers supported for uint64_t and int64_t, respectively:
```

18446744073709551615
923372036854775807

```

---

### Post by OVERPOWER8 on 2009-12-18
Is there a way I can define uint64_t maximum to desired value?

using 

#define **UINT64_MAX**       	 	 	 	 	1844674587454754874073  (example)
or
define **INT64_MAX**      	 	 	 	 	1844674587454754874073

---

### Post by dwhitney67 on 2009-12-18
> **OVERPOWER8 said:**
> Is there a way I can define uint64_t maximum to desired value?

using 

#define **UINT64_MAX**       	 	 	 	 	1844674587454754874073  (example)
or
define **INT64_MAX**      	 	 	 	 	1844674587454754874073

Place a ULL at the the end of the number!  Was this not already discussed in a previous post???????

Frankly, though, if you are developing a C++ application, there is no need to define these macros.

P.S.  A signed-int64_t will *not* hold the value 18446744073709551615; it is too big!  A signed number 'loses' the use of the most significant bit so that it can be used to denote the sign (plus or minus) of the number.

---

### Post by MadCow108 on 2009-12-18
> **OVERPOWER8 said:**
> Thanks, but that's only long long.


I need to use also uint64_t with much greater numbers.
How can I do this?

uint64_t is just a typedef for unsigned long long in gcc
[http://linux.die.net/man/3/uint64_t](http://linux.die.net/man/3/uint64_t)
long long is the C99 64 bit integer data type
gcc also provides this type for C++

for larger numbers you need a big number library (or a 128bit or higher architecture with an appropriate compiler)

---

### Post by LKjell on 2009-12-18
I recently wrote a pi program in Java. What I did to handle long numbers what to split the numbers in arrays. So assume if I have 923372036854775807

If you want to initialize the numbers you just write a function that convert string to the int array.

```
number[0] = 92
number[1] = 3372
number[2] = 0368
number[3] = 5477
number[4] = 5807
```

---

### Post by MadCow108 on 2009-12-18
there are lots of libraries which do that.
You should prefer those over trying yourself (except as an exercise of course) because most libraries use highly sophisticated algorithms to archive a quite good speed.

examples for c++ would be GMP and CLN

---

### Post by quip on 2009-12-18
> **LKjell said:**
> I recently wrote a pi program in Java. What I did to handle long numbers what to split the numbers in arrays. So assume if I have 923372036854775807

If you want to initialize the numbers you just write a function that convert string to the int array.

```
number[0] = 92
number[1] = 3372
number[2] = 0368
number[3] = 5477
number[4] = 5807
```

So, what do you do when you have to execute a mathematical operation on two of these numbers that are in different int arrays?

You can hold a number in the manner you suggest, but you are in effect just treating it as a string.

BTW, it's good to see someone stretching themselves out and trying to code solutions for themselves, but if you are using Java (as you are, but not the OP), you can use the BigInteger class to not only store ints bigger than 64 bits, but also conduct basic arithmetic on them.  For C, I think you might need to look at some math "tricks".  Maybe use logarithms, similar to what a slide rule used to do?  Then you could do the math, and convert to array/string notation for printing output.

---

### Post by LKjell on 2009-12-18
> **quip said:**
> So, what do you do when you have to execute a mathematical operation on two of these numbers that are in different int arrays?

You can hold a number in the manner you suggest, but you are in effect just treating it as a string.

BTW, it's good to see someone stretching themselves out and trying to code solutions for themselves, but if you are using Java (as you are, but not the OP), you can use the BigInteger class to not only store ints bigger than 64 bits, but also conduct basic arithmetic on them.  For C, I think you might need to look at some math "tricks".  Maybe use logarithms, similar to what a slide rule used to do?  Then you could do the math, and convert to array/string notation for printing output.

Make a function to do basic arithmetic and remainder control. Then you loop the array which has the biggest array then stop when you come to the one with smallest.

---

### Post by kwyto on 2009-12-18
in order to handle big numbers like 100 digits or whatever you like, LKjell is right you have to split them up into something that can be handled. i had to do the same for an assembly class i took. basically split them up into pieces of 4 digits put them in a array and perform the operation you want on each of the pieces, every time there is an overflow carry it onto the next piece. save the result in another array and display it later.

---

### Post by quip on 2009-12-18
> **LKjell said:**
> Make a function to do basic arithmetic and remainder control.  Then you loop the array which has the biggest array then stop when you come to the one with smallest.

I am not sure what you mean by the second sentence, but as I said, it can be done--just not that easily in C for a novice programmer.  Also, the person I quoted was using Java, and would have a much easier time using BigInteger as I mentioned.

Also, if you don't mind, I would like to see the function that does multiplication, division, addition, subtraction, and comparisons with arbitrarily large ints.  Doable (several languages have this functionality), but not as easy as people suspect.

Kwyto:

It sounds like you are talking about a basic adder using the individual bits.  I, too, did similar things for a computer organization class that used a lot of assembly, like multiplying two 32 bit ints to produce a 64 bit int.  But it's always the little things, like how to "borrow" during division, or when one number has many more/fewer digits than the other, etc., that pop up and bite you.  Also, if you get one array out of place, you're screwed, because each of the numbers in each array represents a different place value.

---

### Post by LKjell on 2009-12-19
> **quip said:**
> I am not sure what you mean by the second sentence, but as I said, it can be done--just not that easily in C for a novice programmer.  Also, the person I quoted was using Java, and would have a much easier time using BigInteger as I mentioned.

Also, if you don't mind, I would like to see the function that does multiplication, division, addition, subtraction, and comparisons with arbitrarily large ints.  Doable (several languages have this functionality), but not as easy as people suspect.


yea I wrote the stuff in Java but did not use BigInteger.

This is an addition function. Thought it lack some overflow check still it will add. If you want to know how to multiply and divide, as MadCow108 said, GMP is a library written in C. [http://gmplib.org/manual/Algorithms.html#Algorithms](http://gmplib.org/manual/Algorithms.html#Algorithms)

```
#define BASE 10000

struct big_int
{
	int *number; 
	size_t size;
};

struct big_int *add(struct big_int *figure, struct big_int *add)
{
	size_t max = (figure->size >= add->size)
			? figure->size:add->size;

	size_t min = (figure->size < add->size)
			? figure->size:add->size;

	int *serie1;
	int *serie2;

	if (max == figure->size) {
		serie1 = figure->number;
		serie2 = add->number;
	} else {
		serie2 = figure->number;
		serie1 = add->number;
	}
	
	struct big_int *sum = malloc(sizeof(struct big_int));
	int *number = malloc(max * sizeof(int));
	int remainder = 0;
	
	for (int i = max - 1, k = min - 1; i >= 0; i--, k--) {
		if(k >= 0) {
			number[i] = serie1[i] + serie2[k] + remainder;

			if (number[i] >= BASE) {
				number[i] -= BASE;
				remainder = 1;
			} else {
				remainder = 0;
			}
		} else {
			if(i >= 0)
				number[i] += remainder;

			break;
		}	
	}
	
	sum->number = number;
	sum->size = max;

	return sum;
}
```

For subtraction.

```

	for (int i = max - 1, k = min - 1; i >= 0; i--, k--) {
		if(k >= 0) {
			number[i] = serie1[i] - serie2[k] + remainder;

			if (number[i] < 0) {
				number[i] += BASE;
				remainder = -1;
			} else {
				remainder = 0;
			}
		} else {
			if(i >= 0)
				number[i] += remainder;

			break;
		}	
	}
```

---

### Post by jpkotta on 2009-12-19
> **MadCow108 said:**
> uint64_t is just a typedef for unsigned long long in gcc
[http://linux.die.net/man/3/uint64_t](http://linux.die.net/man/3/uint64_t)
long long is the C99 64 bit integer data type
gcc also provides this type for C++

for larger numbers you need a big number library (or a 128bit or higher architecture with an appropriate compiler)

long long is *at least* 64 bits.  It is architecture and implementation dependent.  uint64_t and int64_t are exactly 64 bits wide.  In practice, they're the same, but you should always declare an int type if you want to hold a number less than some value, and an intxx_t type if you want to hold a certain number of bits.

---

### Post by quip on 2009-12-19
> **LKjell said:**
> yea I wrote the stuff in Java but did not use BigInteger.

code snipped...


As I said, doable, but not easy for a novice to implement in C.  You are certainly no novice, but just in the addition function:

1.  As you mentioned, no overflows are not checked.  This is a problem, especially if, say, 2 numbers, each of the max size, are added together.  Anything that adds to 10 or greater in the most significant array (for lack of a better term) would overflow its remainder out, which your code can't represent.  

2.  You need to clear the remainder after using it in your else block, otherwise it could keep carrying out and out, getting added to arrays that it wasn't supposed to.  Example--using base 10^4, as you did, 2222222222 + 8888.  It carries to the middle 4 8s, but then also to the last 2, where it shouldn't be.

3.  If the 2 numbers to add are equal in size, your min value will not be set.  You could remedy this with a simple <= in place of your < in the true/false conditional.

Now, the second 2 points are easily fixed, and the first one can be, but the point I was trying to make is that, for someone who is not used to dealing with these types of problems, bugs can creep in awfully easy.  

Also, when I said math "tricks", I wasn't specifying that the solution need be incredibly clever; just that it exploited the ability to evaluate the operations as having more or less value than they actually have in the real number--such as changing the base, as you did.

I did not look at the subtraction code.  However, I just feel that, given all these pesky little bugs popping up in just the simplest of operations (addition, although multiplication can really be thought of a repetitive addition problem), the chance of making errors in more difficult but often used math operations is quite high.  That's why, for most instances, it is wiser to use a rigid, tested, tried-and-true implementation that has already been written--like BigInteger, if using Java.

---

### Post by LKjell on 2009-12-19
> **quip said:**
> As I said, doable, but not easy for a novice to implement in C.  You are certainly no novice, but just in the addition function:

1.  As you mentioned, no overflows are not checked.  This is a problem, especially if, say, 2 numbers, each of the max size, are added together.  Anything that adds to 10 or greater in the most significant array (for lack of a better term) would overflow its remainder out, which your code can't represent.  

2.  You need to clear the remainder after using it in your else block, otherwise it could keep carrying out and out, getting added to arrays that it wasn't supposed to.  Example--using base 10^4, as you did, 2222222222 + 8888.  It carries to the middle 4 8s, but then also to the last 2, where it shouldn't be.

3.  If the 2 numbers to add are equal in size, your min value will not be set.  You could remedy this with a simple <= in place of your < in the true/false conditional.

Now, the second 2 points are easily fixed, and the first one can be, but the point I was trying to make is that, for someone who is not used to dealing with these types of problems, bugs can creep in awfully easy.  

Also, when I said math "tricks", I wasn't specifying that the solution need be incredibly clever; just that it exploited the ability to evaluate the operations as having more or less value than they actually have in the real number--such as changing the base, as you did.

I did not look at the subtraction code.  However, I just feel that, given all these pesky little bugs popping up in just the simplest of operations (addition, although multiplication can really be thought of a repetitive addition problem), the chance of making errors in more difficult but often used math operations is quite high.  That's why, for most instances, it is wiser to use a rigid, tested, tried-and-true implementation that has already been written--like BigInteger, if using Java.

Maybe I was too hasty. But I forgot a big chunk to make it usable.

The min value and max value is always set. Even if the arrays have the same size. Say that you have a is equal to b. a < b ? a : b .
Does not matter whether you return a or b since they have the same size.

For addition. Fixes are in red.
```

	for (int i = max - 1, k = min - 1; i >= 0; i--, k--) {
		if(k >= 0) {
			number[i] = serie1[i] + serie2[k] + remainder;

			if (number[i] >= BASE) {
				number[i] -= BASE;
				remainder = 1;
			} else {
				remainder = 0;
			}
		} else {
[COLOR="Red"]			number[i] = serie1[i] + remainder;

			if (number[i] >= BASE) {
				number[i] -= BASE;
				remainder = 1;
			} else {
				remainder = 0;
			}[/COLOR]
		}	
	}
```

---

### Post by quip on 2009-12-19
> **LKjell said:**
> 
The min value and max value is always set.

You are correct.  I, too, was hasty in my review of your code, and I do not usually use the conditional syntax that you do.  If the second test fails (the one to set the min), then add->size will be fed in, and it will get set.  My bad.

---

### Post by rfoxmich on 2012-09-04
To do this you must define (e.g. -D or #define)

__STD_CONSTANT_MACROS

prior to the inclusion.


> **Habbit said:**
> Using the C99 include file <stdint.h>, which will also be part of the next C++ standard as <cstdint>, you can use the standard integer constant macros, which transform the integer constant into the appropriate format for the type by appending the required suffixes. For example:```
#include <cstdint>

int main() {
    uint64_t n = UINT64_C(18446744073709551615);
    int64_t  m =  INT64_C(0x8000000000000000);
    return 0;
}
```

The [u]intN_t types and its associated macros translate into different things depending on the architecture. For example, on my 32bit Windows box, a 64-bit integer is an "[unsigned] long long", and thus the suffix appended is [u]LL, but in my 64-bit Ubuntu box it is a normal "[unsigned] long", so the suffix is simply [u]L.

---

