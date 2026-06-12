---
title: "C: Problem in output &amp; give an accuracy of one decimal place"
date: 2008-09-14
forum: Programming Talk
---

### Post by her_ron_potter on 2008-09-14
I'm coding C. And I have 2 problems need to be solved :confused:

The exercise is: Write a program which will take the input as a floating point number. This number represents the centimeters. Print out the equivalent number of feet, with feet given to an accuracy of one decimal place.

1. 
This is my code:

```
#include <stdio.h>
void main()
{
	//Declare variables
	float a;

	//Take the input as a floating point number
	printf("\n Enter a real number: ");
	scanf("%f", &a); //The number represents cm and passed into the "a" variable

	//Exchange cm to feet
	float f;
	f = a / (12 * 2.54) ;
	printf (**[COLOR="Red"]"cm[/COLOR]** = %f feet", f);
}
```

The problem is red color, I don't know how to print out the number that user input before the **cm**.  can u tell me how to include the variable **a** in the screen
[I]Assume user input 333.3, and I want the screen must show:
333.3 cm is 10.9 feet[/I]
In this case, 333.3 is value of **a** variable.

2. How to Print out the equivalent number of feet, with feet **given to an accuracy of one decimal place**. 
If the input value is 333.**3333333**, the output format should be: 333.**3** (only 1 decimal).

Plz help me
Thanks in advance
Sorry for my bad English :(

---

### Post by engineer on 2008-09-14
is this what you're looking for?
```

printf("%f cm - %f feet", a, f);

```

the precision can be set by additional arguments to the format string.

in your case

```

printf("%f cm - %.1f feet", a, f);

```

---

### Post by her_ron_potter on 2008-09-14
Hi!
Thank for ur help. I did it successfully. But when I print out the result, the **a** variable had many decimal place, such as:

When I input the number **333.3**, it showed:
[B]
333.299988 cm is 10.9 feet
[/B]
But I just want it to show 333.3.

Another case:
When user input **333.33333,** it showed

**333.333344 cm is 10.9 feet**

I want it to show the result: **333.33333** (as user input, no change). 
Can u help me to fix it?  Thanks

---

### Post by dwhitney67 on 2008-09-14
Make this helpful guide your "friend":  [http://www.cppreference.com/stdio/printf.html](http://www.cppreference.com/stdio/printf.html)

To answer your question more specifically, try something like:
[PHP]printf( "%1.1f\n", myFloatValue );[/PHP]

---

### Post by her_ron_potter on 2008-09-14
```
 printf( "%[COLOR="Red"]1.1[/COLOR]f\n", myFloatValue ); 
```
This code worked only when the user input a floating point number with **one** decimal place, such as: 333.**3**, 1.**4**, 542.**6**. I want the result print out indepent on that. Such as if the user input 3.4444 then the result show: 3.4444, the user input 764.839284928 then the result still show 764.839284928, with no change.
When I tried your code, when I input 333.**3333** (4 decimal place) it showed only 333.**3** (only 1 decimal place).
How can I do that?

---

### Post by dwhitney67 on 2008-09-14
The '1.1' sandwiched between the '%' and the 'f' indicates to show a floating-point value with a tolerance of up to one decimal place (tenths).

If you wish to see all the digits, then remove the '1.1'.  For example:
[PHP]printf( "%f cm = %0.1 feet\n", cm, feet );[/PHP]
If you wish to limit the number of decimal places for the centimeter value, then make the appropriate change.

One thing that you need to understand is that it is probably impossible for a typical computer to retain the precision you desire in a floating point value.  Perhaps you should consider using a double.

Here's a complete example:
[PHP]#include <stdio.h>

int main()
{
  double cm = 0.0;

  printf( "Enter the centimeters (cm): " );
  scanf( "%lf", &cm );

  double feet = cm / (12.0 * 2.54);

  printf( "%lf cm = %0.1lf feet\n", cm, feet );

  return 0;
}[/PHP]

---

### Post by Tony Flury on 2008-09-15
Does anyone else think that this smacks of a school/college assingment ?

Apologies to the OP if it is not a homework assignment, but it does seem odd if it is not ?

In the spirit of it being a school/college assignment, you might want to think about this : 

When you use scanf the library takes the characters the user types in, and converts them to your required input (in your case a double). It then throws the actual characters away, and you are just left with the convereted value - and this conversion can be not particularly accurate.

If you want to actually output what the user types in, you need to make sure you access the characters that they type - i.e. don't let scanf do the conversion - do it yourself after you have captured the characters.

---

### Post by dwhitney67 on 2008-09-15
Yes, it does look like an assignment.  I for one get annoyed when a trivial problem is presented and last through 3 or more posts.  Hence the reason I gave the solution.

I do not care if the OP is indeed in a C programming course.  I do not fear competition from him/her in the workplace.

Let it be a warning/advice to all junior programmers... do some research on your own before bringing simplistic problems to a forum.  You might get offended by some harsh criticism... not from me, but from others.  It goes with the territory.


P.S.  The dumbest question I have been asked was from a junior colleague, who happened to a graduate from Cal Poly (Pomona) -- Master's Degree in CS -- "What's the character (in C) for a carriage-return?"

Another colleague and I looked at each other in amazement that someone, with educational credentials, would ask such as silly question.  Could it be a trick question was the first thing that came to mind???

---

### Post by cszikszoy on 2008-09-15
> **dwhitney67 said:**
> P.S.  The dumbest I have been asked was from a junior colleague, who happened to a graduate from Cal Poly (Pomona) -- Master's Degree in CS -- "What's the character (in C) for a carriage-return?"

That's pathetic.  What a sad way to represent my school :(

Oh well, at least in the College of Engineering they actually teach people how to program.

---

### Post by dwhitney67 on 2008-09-15
The fact that this recent graduate from Cal Poly didn't know the answer was not what perplexed me.  What did bother me was the fact she didn't even take the time (1 minute??) to Google for the answer.

Independent research is an art that I supposed has been lost by many students.

---

### Post by her_ron_potter on 2008-09-15
:D
Thank for all ur help. I will try it
But to all: I'm not learning about technology, I'm learning economic. Last week, I borrowed a book about programming in C from my friends, and I'm learning it by myself. The question is only a small excercise in the book, not an assignment in school/colleage.
Because I don't learn about technology, so I'm just an amateur in programming, I just learn programming because of my hobby, I find it interesting ^^.
Finally, I appology to all people, because of my silly question...
I'm only an amateur :((

P/S: Does anybody have an useful link/web guide about C? Can you share with me? Thanks

---

### Post by stevescripts on 2008-09-15
> **her_ron_potter said:**
> :D

P/S: Does anybody have an useful link/web guide about C? Can you share with me? Thanks

Did you READ THE STICKIES?  

Everything you need to start (and more) is there.

Steve

---

### Post by dribeas on 2008-09-15
> **her_ron_potter said:**
> When I input the number **333.3**, it showed:
[B]
333.299988 cm is 10.9 feet
[/B]
But I just want it to show 333.3.


> **her_ron_potter said:**
> I want the result print out indepent on that. Such as if the user input 3.4444 then the result show: 3.4444, the user input 764.839284928 then the result still show 764.839284928, with no change.

While it does indeed look like homework and so I would not answer the original post, this last part is interesting. You have two problems, first one is that cannot know the input decimal digit number, only the converted value. That is, if the user enters three decimal digits, you won't know, whether you want three, two or five digits in your output -unless, of course, you read into a string (char*) and then convert to floating point with atof()--.

The second part is with precision. Floating point numbers are represented with a fixed number of bits and you cannot possibly represent all real numbers (infinite number of them in any given interval), only a subset. That is the reason why 333.3 may internally be represented with 333.299988.

If you want to know more about floating point representation, most systems use IEEE 754 standard, google for it.

---

