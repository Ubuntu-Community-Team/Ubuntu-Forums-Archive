---
title: "Puzzling Long Long Int Behavior"
date: 2009-06-20
forum: Programming Talk
---

### Post by nmccrina on 2009-06-20
Hi!

I was writing a program to factor a number into its prime factors. It actually mostly works. Here is the code:

```

#include <stdio.h>

void getLowestPrimeFactor(long long int num);

int main(int argc, char* argv[])
{
	/* Convert the number given as a parameter to an int */
	long long int num = atoll(argv[1]);
	
	printf("\n");
	
	/* If the number is 0 or 1, simply print that number */
	if (num > -1 && num < 2)
	{
		printf("\n%llu\n\n", num);
	}	
	/* If the number is two or greater, find a number that divides 
		evenly into the value of the num variable (the number we 
		are factoring), increasing the divisor from 2. 
                The smallest 
		number that divides evenly into the value of the num 
		variable is guaranteed to be prime, and we can list it as 
		one of the prime factors. Factor it out, then try to find 
		more prime factors. We repeat this until the value 
		of the num variable is prime, and it becomes the final 
		prime factor. This is all done recursively by the
		getLowestPrimeFactor() function. */
	else if (num > 1)
	{
		getLowestPrimeFactor(num);
	}
	
	printf("\n\n");
	
	return 0;
}

void getLowestPrimeFactor(long long int num)
{
	long long int i = 0;
	for (i = 2; i <= num; i++)
	{
		/* The first value of i that evenly divides the 
			value of num is a prime factor of num */
		if (!(num % i))
		{
			printf("%llu", i);
			/* If the value of i equals the value of num 
				(that is, there is no value less than num 
				that evenly divides num), we have found 
				the last prime factor, and we return. 
				Otherwise, factor out the prime factor we 
				just found by dividing num by it, and run 
				the function again looking for more    factors */
			if (num == i)
			{
				return;
			}
			else
			{
				printf("%s", "x");
				num = num / i;
				getLowestPrimeFactor(num);
			}
			return;
		}
	}	
}			}
			else
			{
				printf("%s", "x");
				num = num / i;
				getLowestPrimeFactor(num);
			}
			return;
		}
	}	
}

```

The problem is, it only works for numbers up to 2^31 :mad: (The actual highest number it factors is 2147483646, or 2^31 - 2). On my machine, the value I get for sizeof(long long int) is 8, so shouldn't it be able to handle numbers up to 2^63? Thanks for helping! :p

---

### Post by slavik on 2009-06-20
also make it unsigned. :) so that you can do anything up to and including 2^64 - 1

---

### Post by lisati on 2009-06-20
> **slavik said:**
> also make it unsigned. :) so that you can do anything up to and including 2^64 - 1

Rats! Beat me to it!

The sign bit will always reduce (um what's the word again?) precision by a factor of two when present.

---

### Post by MadCow108 on 2009-06-20
for even bigger numbers you could use a big number library like cln:
[http://www.ginac.de/CLN/](http://www.ginac.de/CLN/)

---

### Post by Bachstelze on 2009-06-20
> **lisati said:**
> The sign bit will always reduce (um what's the word again?) precision by a factor of two when present.

It's not really relevant to speak of "precision" about integers, and integer is an integer. The ranges of values you can code with signed and unsigned integers have the same width, they are just positioned differently (in one case, zero is at the middle of it, in the other it's its lowest value).

---

### Post by nmccrina on 2009-06-20
Thanks for the replies! Sorry for the long delay, but I went out and played a tennis match :D 

Unfortunately, the unsigned thing didn't work. :( 

I modified the code thusly: 

```

#include <stdio.h>
#include <stdlib.h>

void getLowestPrimeFactor(unsigned long long int num);

int main(int argc, char* argv[])
{
	/* Convert the number given as a parameter to an int */
	unsigned long long int num = atoll(argv[1]);
	
	printf("\n");
	
	/* If the number is 0 or 1, simply print that number */
	if (num > -1 && num < 2)
	{
		printf("\n%llu\n\n", num);
	}	
	/* If the number is two or greater, find a number that divides 
		evenly into the value of the num variable (the number we 
		are factoring), increasing the divisor from 2. The smallest 
		number that divides evenly into the value of the num 
		variable is guaranteed to be prime, and we can list it as 
		one of the prime factors. Factor it out, then try to find 
		more prime factors. We repeat this until the value 
		of the num variable is prime, and it becomes the final 
		prime factor. This is all done recursively by the
		getLowestPrimeFactor() function. */
	else if (num > 1)
	{
		getLowestPrimeFactor(num);
	}
	
	printf("\n\n");
	
	return 0;
}

void getLowestPrimeFactor(unsigned long long int num)
{
	unsigned long long int i = 0;
	for (i = 2; i <= num; i++)
	{
		/* The first value of i that evenly divides the 
			value of num is a prime factor of num */
		if (!(num % i))
		{
			printf("%llu", i);
			/* If the value of i equals the value of num 
				(that is, there is no value less than num 
				that evenly divides num), we have found 
				the last prime factor, and we return. 
				Otherwise, factor out the prime factor we 
				just found by dividing num by it, and run 
				the function again looking for more factors */
			if (num == i)
			{
				return;
			}
			else
			{
				printf("%s", "x");
				num = num / i;
				getLowestPrimeFactor(num);
			}
			return;
		}
	}	
}

```

Basically, I just replaced "long long int" with "unsigned long long int". That didn't work. I also tried to use c99 mode, which changed nothing except that it generated a warning of an "implicit definition of atoll()". So I included stdlib.h which fixed the warning, but still produced the same (non) results. 

That said, is the fact that my computer is 32-bit have anything to do with it? Should I have mentioned that at the beginning? :p

---

### Post by Victor Liu on 2009-06-20
When I try running your code with an input larger than 2^31, the [FONT="Courier New"]atoll[/FONT] function appears to return an incorrect result. For me, when I print out [FONT="Courier New"]num[/FONT] right after it was read in, the result is incorrect.

Barring that, I had to change all instances of [FONT="Courier New"]long long int num[/FONT] to [FONT="Courier New"]long long unsigned int num[/FONT] to get the code to run properly (it thought num was negative and never entered either branch in main). Of course it runs properly on an unintended input, so you'll have to implement your own simple string-to-number conversion.

---

### Post by lloyd_b on 2009-06-20
Your problem isn't actually with the long long int - there seems to be a problem with atoll().  Put a printf() into the program immediately after the conversion, to display the value of "num", and you'll see what I mean.

Lloyd B.

Edit - Victor Liu beat me to it :)

---

### Post by nmccrina on 2009-06-20
> **Victor Liu said:**
> When I try running your code with an input larger than 2^31, the [FONT="Courier New"]atoll[/FONT] function appears to return an incorrect result. For me, when I print out [FONT="Courier New"]num[/FONT] right after it was read in, the result is incorrect.


Okay, one difference is that when I run it with an input larger than 2^31, I get, not just an incorrect result, but no result at all (it just exhibits endless-loop-like symptoms). 

> 
Barring that, I had to change all instances of [FONT="Courier New"]long long int num[/FONT] to [FONT="Courier New"]long long unsigned int num[/FONT] to get the code to run properly (it thought num was negative and never entered either branch in main).

I'm not sure what the issue was, here. All numbers 2^31 - 2 and below work fine for me using [FONT="Courier New"]unsigned long long int[/FONT] or [FONT="Courier New"]long long unsigned int[/FONT]

---

### Post by nmccrina on 2009-06-20
> **lloyd_b said:**
> Your problem isn't actually with the long long int - there seems to be a problem with atoll().  Put a printf() into the program immediately after the conversion, to display the value of "num", and you'll see what I mean.

Lloyd B.

Edit - Victor Liu beat me to it :)

I did that, and it was fine :confused:

---

### Post by Victor Liu on 2009-06-20
This works for me (on Cygwin w/ Vista):

```

#include <stdio.h>

void getLowestPrimeFactor(long long int num);

// assumes str is just a string of digits; dangerous!
long long unsigned int string_to_llu(char *str){
	long long unsigned int result = 0;
	while(*str != '\0'){
		result *= 10;
		result += (*str - '0');
		++str;
	}
	return result;
}

int main(int argc, char* argv[])
{
	/* Convert the number given as a parameter to an int */
	//long long int num = atoll(argv[1]);
	long long unsigned int num = string_to_llu(argv[1]);
	
	printf("%llu\n", num);
	
	/* If the number is 0 or 1, simply print that number */
	if (num > -1 && num < 2)
	{
		printf("\n%llu\n\n", num);
	}	
	/* If the number is two or greater, find a number that divides 
		evenly into the value of the num variable (the number we 
		are factoring), increasing the divisor from 2. 
                The smallest 
		number that divides evenly into the value of the num 
		variable is guaranteed to be prime, and we can list it as 
		one of the prime factors. Factor it out, then try to find 
		more prime factors. We repeat this until the value 
		of the num variable is prime, and it becomes the final 
		prime factor. This is all done recursively by the
		getLowestPrimeFactor() function. */
	else if (num > 1)
	{
		getLowestPrimeFactor(num);
	}
	
	printf("\n\n");
	
	return 0;
}

void getLowestPrimeFactor(long long int num)
{
	long long unsigned int i = 0;
	for (i = 2; i <= num; i++)
	{
		/* The first value of i that evenly divides the 
			value of num is a prime factor of num */
		if (!(num % i))
		{
			printf("%llu", i);
			/* If the value of i equals the value of num 
				(that is, there is no value less than num 
				that evenly divides num), we have found 
				the last prime factor, and we return. 
				Otherwise, factor out the prime factor we 
				just found by dividing num by it, and run 
				the function again looking for more    factors */
			if (num == i)
			{
				return;
			}
			else
			{
				printf("%s", "x");
				num = num / i;
				getLowestPrimeFactor(num);
			}
			return;
		}
	}	
}

```

Note that in your loop in getLowestPrimeFactor, you only need to check up to sqrt(num) rather than num. If that's too difficult, then at least cut it off at num/2.

---

### Post by lloyd_b on 2009-06-20
> **nmccrina said:**
> I did that, and it was fine :confused:

First problem - your original post did not have "#include <stdlib.h>" in it.  Strangely enough, it still allowed the use of the atoll() function, but without that include file atoll() produces garbage results for numbers larger than 2^31.  So that's one difference.

Using your most recent code (with the #include <stdlib.h>), it seems to be working fine on my machine:```
lloyd@dell:~/stuff$ ./test 3000000000

2x2x2x2x2x2x2x2x2x3x5x5x5x5x5x5x5x5x5

lloyd@dell:~/stuff$ ./test 3150222333

3x1050074111
```Note that this is being run on a 32 bit Celeron machine.

Lloyd B.

---

### Post by Victor Liu on 2009-06-20
> **lloyd_b said:**
> First problem - your original post did not have "#include <stdlib.h>" in it.  Strangely enough, it still allowed the use of the atoll() function, but without that include file atoll() produces garbage results for numbers larger than 2^31.  So that's one difference.

Ah, good catch. Without the declaration, it is assumed that a function returns an int, which would explain the results.

---

### Post by nmccrina on 2009-06-20
> **lloyd_b said:**
> 
Using your most recent code (with the #include <stdlib.h>), it seems to be working fine on my machine.

Note that this is being run on a 32 bit Celeron machine.

Lloyd B. 

Gaaah! :lolflag: That is really strange! I can't think of anything else to try. I incorporated V. Liu's new string_to_llu function, but it didn't change anything. Like I said, it is outputting the numbers fine, even the ones over 2147483646, but over that number it just appears to go into some kind of endless loop instead of printing the factors. I have to ctrl-c to exit the program.

Thanks for all the suggestions so far, guys! :popcorn:

---

### Post by nmccrina on 2009-06-20
> **Victor Liu said:**
> T
Note that in your loop in getLowestPrimeFactor, you only need to check up to sqrt(num) rather than num. If that's too difficult, then at least cut it off at num/2.

I did this, using:

```
for (i = 2; i <= (long long unsigned int)sqrt((double)num); i++)
```

Now it seems to work completely. Apparently the problem was simply the for loop taking too long when trying to factor large prime numbers. 

I feel pretty dumb. :P

---

