---
title: "Binomial Theorem - Inaccurate output in a  C program"
date: 2007-02-15
forum: Programming Talk
---

### Post by sympeltun on 2007-02-15
hi guys,

i was given an assignment to compute the result of the binomial theorem, using the formula. i did finish the program however i found that the output was being in accurate by a small decimal point. the thing is that one of the teachers said that i'll still get the mark for a close enough value (because they're being easy on the lab..) but i really would like to know how to overcome the inaccuracy that's happening.. i have posted the code below and i will put the output as well. i know my professor told us that there was a way to overcome it, i cant find those notes at this time, and im hoping someone could help me with this.

As far as the code is concerned, im pretty sure that there's nothing wrong with it. im 

My code:
```
#include <stdio.h>

#include <math.h>

int

main()



{

	double b, n, i, j, numerator, denominator, coefficient, total;

	numerator = 1;

	denominator = 1;

	total =0;



	printf("Please enter a value for b between 0 and 1:  ");

	scanf("%lf", &b);

	

	



	while (b <= 0 || b >= 1)

	{

		

		printf("\nPlease enter a value for b between 0 and 1:  ");

		scanf("%lf", &b);



	}

	printf("\nPlease enter an value for n:  ");

	scanf("%lf", &n);



	for (i = 0; i < n; ++i)

	{

		

		



		for (j = 0; j < i; ++j)

		{

			

			numerator = numerator*(n-j);

			denominator = denominator*(j+1);

			

		}



		coefficient = numerator/denominator;

		total = total + coefficient*pow(1,(n-i))*pow(b,i);

	}

	

	printf("\nThe total of (1 + %f)^%f is %f	(using the binomial theorem)\n", b, n, total);

	printf("The total without using the binomial theorem is %f", pow((1+b),n));



	return (0);



}
```

The output - 

```
Please enter a value for b between 0 and 1:   0.6



Please enter a value for n:  5



The total of (1 + 0.600000)^5.000000 is 1.400000	(using the binomial

theorem)

The total without using the binomial theorem is 1.440000
```

your help is very much appreciated!

Sai

---

### Post by WW on 2007-02-15
Your output doesn't agree with the output that I get when I run your code, and in fact, the result that your output shows is not correct, since (1.6)^5 = 10.48576.

There are two problems with your code.  First, you have an 'off-by-one' error: the i loop should be 'for (i = 0; i <= n; ++i)'.  Second, you must reinitialize numerator and denominator to 1 before entering the j loop.

Here's a revised version:
```

#include <stdio.h>
#include <math.h>

int
main()
{
	double b, n, i, j, numerator, denominator, coefficient, total;
	total =0;
	printf("Please enter a value for b between 0 and 1:  ");
	scanf("%lf", &b);
	while (b <= 0 || b >= 1)
	{
		printf("\nPlease enter a value for b between 0 and 1:  ");
		scanf("%lf", &b);
	}
	printf("\nPlease enter an value for n:  ");
	scanf("%lf", &n);
	for (i = 0; i <= n; ++i)
	{
		numerator = 1;
		denominator = 1;
		for (j = 0; j < i; ++j)
		{
			numerator = numerator*(n-j);
			denominator = denominator*(j+1);
		}
		coefficient = numerator/denominator;
		total = total + coefficient*pow(1,(n-i))*pow(b,i);
	}
	printf("\nThe total of (1 + %f)^%f is %f	(using the binomial theorem)\n", b, n, total);
	printf("The total without using the binomial theorem is %f\n", pow((1+b),n));
	return (0);
}

```
And here is your example:
> 
Please enter a value for b between 0 and 1:  0.6

Please enter an value for n:  5

The total of (1 + 0.600000)^5.000000 is 10.485760       (using the binomial theorem)
The total without using the binomial theorem is 10.485760


---

### Post by sympeltun on 2007-02-16
thanks for helping me out, it's hard to believe that simple mistakes like that costed me a lot of time yesterday lol

Sai

---

