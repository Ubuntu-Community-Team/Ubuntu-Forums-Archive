---
title: "precision of numbers representation"
date: 2010-01-09
forum: Programming Talk
---

### Post by cyprys on 2010-01-09
Hi there,

I recently hear a lot about many ways of representing numbers in applications (which is easy to understand since there are several types of number variables like int, float and double) but what's about all that precision talking?

Can someone write a simple example in C/C++ showing differences between precision of int, float and double variable types? Does that regard amount of decimal spaces?

Pointing to some online reading material would also be awesome.

Thanks,
Cyprian

---

### Post by Zugzwang on 2010-01-09
> **cyprys said:**
> 
Pointing to some online reading material would also be awesome.


This should be helpful: [http://en.wikipedia.org/wiki/Floating_point](http://en.wikipedia.org/wiki/Floating_point)

---

### Post by gvoima on 2010-01-09
In short:
Precision is the total number of significant decimal digits.
Accuracy is the number of significant decimal digits to the right of the decimal point.

---

### Post by cyprys on 2010-01-09
I stumbled on difficulties in understanding this wikipedia article. I think my English is simply to weak.

Begging for an example in C/C++ as it can explain more than a thousand words to me.

---

### Post by Zugzwang on 2010-01-09
> **cyprys said:**
> I stumbled on difficulties in understanding this wikipedia article. I think my English is simply to weak.


Did you try the polish version of the article? As far as I can tell from the formulas, the basic concepts are also explained there.

---

### Post by cyprys on 2010-01-09
Yes, I did read the Polish version but it doesn't explain where the difference between common methods of representing numbers come from - it basically says how those numbers are stored in memory.

I still need some clarification on ["Minimizing the effect of accuracy problems"](http://en.wikipedia.org/wiki/Floating_point#Minimizing_the_effect_of_accuracy_problems) section of wikipedia "Floating Point" article.

Especially, I do not understand why there's a difference in results between two recursive forms of 6*2^i*t[i] . Both numbers are stored in the same type of variable, so why?

---

### Post by Finalfantasykid on 2010-01-09
I'm not sure if writting some code is the best way to explain it.

Basically, an int is a 32 bit whole number, a float is a 32 bit real number(it's not actually real since it has gaps), and double is 64 bit with the same story as a float.

Just as a simple example, the number 10 has less precision than the number 10.102.  Similarly, 10.102 has less precision than the number 10.102003405.  The more bits you have, the more significant decimal places you are able to represent.

Most of the time, you don't really need to worry about precision as 32 bits is plenty to deal with for most applications.  You might want to use doubles for very complex calculations which involve very precise measurements.

---

### Post by dribeas on 2010-01-09
> **gvoima said:**
> In short:
Precision is the total number of significant decimal digits.
Accuracy is the number of significant decimal digits to the right of the decimal point.

Precision refers to the total number of significant digits (whether in the integer or decimal part). Accuracy relates of how close to reality those digits are.

Example: The temperature is 25.63 ºC and you have two termometers. One of them is an old analog mercurial bar that only has degree scale and sets somewhere between 25 and 26 degrees. The other termometer is a digital one giving a reading of 24.987. The first instrument is accurate even if not precise, while the second instrument is precise (more number of significant digits) but less accurate.

---

### Post by cyprys on 2010-01-09
> **Finalfantasykid said:**
> I'm not sure if writting some code is the best way to explain it.
I disagree.

[php]// An example in C.

#include "stdio.h"


int main() {
	double l = 0.1, l3 = 0.1;
	float l2 = 0.1, l4 = 0.1;

	int i, counter;

#define VALUE 0.1

	float fl = VALUE;
	double d = VALUE;
	double	tmp1=0, tmp2=0, tmp3=0, tmp7 = 0,tmp8 = 0,tmp9 = 0;
	float	tmp4=0, tmp5=0, tmp6=0, tmp10= 0,tmp11= 0,tmp12= 0;

	printf("\n%f representation -- float: %8X, double: %16llX\n\n",fl, *(int *)&fl, *(long long *)&d); 

	for (counter=0; counter < 50; ++counter) {
		tmp1 = 3.0 * l;
		tmp2 = 1 - l;
		tmp3 = tmp1 * tmp2;
		l = l + tmp3;
 
		tmp4 = 3.0 * l2;
		tmp5 = 1 - l2;
		tmp6 = tmp4 * tmp5;
		l2 = l2 + tmp6;
	
		tmp7 = 4 * l3;
		tmp8 = 3 * l3;
		tmp9 = tmp8 * l3;
		l3 = tmp7 - tmp9;

		tmp10 = 4 * l4;
		tmp11 = 3 * l4;
		tmp12 = tmp11 * l4;
		l4 = tmp10 - tmp12;

		printf ("counter %d   double %f    float %f   %d      double %f     float%f\n", counter, l, l2, counter, l3, l4);
	}

	float e = 1.0, eold = e;

	while ((1.0+e) > 1.0) {
		eold = e;
		e /= 2;
	}

	printf ("mantissa = %4.50f\n", eold);

	return 0;
}[/php]

See? :) Feel free to optimize and correct my mistakes (I know it's messy and I will actually be happy to see it optimized to learn something).

And I'm not sure if I understand correctly what the following does:```
*(type *)&val
```I think it points to the reference of "val" variable and treats it as "type", am I right? Just found such expression on google's code search engine without any comment but it seemed to be the right one and it worked (amazingly).

---

### Post by MadCow108 on 2010-01-09
> **cyprys said:**
> Especially, I do not understand why there's a difference in results between two recursive forms of 6*2^i*t[i] . Both numbers are stored in the same type of variable, so why?

the reason is explained beneath table of numbers. It has nothing to do with the representation in a computer (as long as the representation has a fixed precision)

you subtract two nearly identical numbers, which is numerically bad.
subtracting near equal numbers leads to a loss if significance
example:
1.543121-1.543113 = 0.0012
if you now calculate with 6 digits precision:
1.54311-1.54312 = 0.001
while the input numbers are relative equal to the real numbers (less than 1%), the result is very far of (~20%)

this is one of the *important rules* you should know for numerical calculations.
Often you can replace subtractions by other mathematical operations, or reorder your terms to avoid this.
prime example of a practical problem where this happens is numerical differentiation. (and is solved by reordering the naive equation)

as stated in the article, getting a numerically stable equation can be tricky and often requires quite a bit of numerical analysis. As a part of mathematics it does often not have much to do with the actual implementation floating numbers in a computer.

---

### Post by cyprys on 2010-01-09
Thank You very much, MadCow108! It's all cleared up now. I was lurking all in wrong directions and the truthful reasoning was so obvious!

Thanks to you too guys: Zugzwang, gvoima, Finalfantasykid, all of you.

---

