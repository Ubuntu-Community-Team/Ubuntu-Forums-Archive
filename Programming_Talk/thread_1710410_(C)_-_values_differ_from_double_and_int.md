---
title: "(C) - values differ from double and int"
date: 2011-03-19
forum: Programming Talk
---

### Post by laus_deo on 2011-03-19
I'll put my whole code down at the bottom, but my main problem is that I have an initial value set as a double in a structure, and then when I transfer it to an int value it changes. 

Heres the code, I have the part setting the pennies edited so that I can see how many pennies the cost would be overall, and though I set total.cost to be 2.36, it keeps outputting that there are only 235 pennies. If I change that to a double, however, it works fine. I could change it if I had to, but I would really like to know whats going on. 


```

#include <stdio.h> 

int main()
{
	struct money
	{
		double total;		
		int dollars;
		int quarters;
		int dimes;
		int nickels;
		int pennies;
	} cost, change; 

	int number, filler;
	float unitPrice = 2.36;

	printf("Welcome to my luxourious bagel shop.");
	printf("How many bagels do you want to buy?");
	printf("They are $2.36 each.\n");
	scanf("%d", &number);

	cost.total = unitPrice * number;
	cost.dollars = cost.total/1;
	cost.quarters = (cost.total - cost.dollars)/.25;
	cost.dimes = (cost.total - cost.dollars - cost.quarters*.25)/.1;
	cost.nickels = (cost.total - cost.dollars - cost.quarters*.25 - cost.dimes*.1)/.05;
	cost.pennies = (cost.total)/.01;


	printf("The total cost is %.2f\n", cost.total);
	printf("%d dollars\n", cost.dollars);
	printf("%d quarters\n", cost.quarters);
	printf("%d dimes\n", cost.dimes);
	printf("%d nickels\n", cost.nickels);
	printf("%d pennies\n", cost.pennies);
	 
}

```

---

### Post by slavik on 2011-03-19
double type cannot accurately describe some decimals.

---

### Post by laus_deo on 2011-03-19
Okay, is that the same with floats, because I decided to switch every double to float and I still get a penny off in the int format, but the right amount for the float format.

---

### Post by slavik on 2011-03-19
yes

doubles and floats are exactly the same, except doubles have more precision. I suggest reading the IEEE specifications for doubles and floats to understand how they work.

---

### Post by Some Penguin on 2011-03-19
Same deal.  Fixed-point arithmetic is used for financial calculations for this reason.

---

### Post by Arndt on 2011-03-20
> **laus_deo said:**
> I'll put my whole code down at the bottom, but my main problem is that I have an initial value set as a double in a structure, and then when I transfer it to an int value it changes. 

Heres the code, I have the part setting the pennies edited so that I can see how many pennies the cost would be overall, and though I set total.cost to be 2.36, it keeps outputting that there are only 235 pennies. If I change that to a double, however, it works fine. I could change it if I had to, but I would really like to know whats going on. 


```

#include <stdio.h> 

int main()
{
	struct money
	{
		double total;		
		int dollars;
		int quarters;
		int dimes;
		int nickels;
		int pennies;
	} cost, change; 

	int number, filler;
	float unitPrice = 2.36;

	printf("Welcome to my luxourious bagel shop.");
	printf("How many bagels do you want to buy?");
	printf("They are $2.36 each.\n");
	scanf("%d", &number);

	cost.total = unitPrice * number;
	cost.dollars = cost.total/1;
	cost.quarters = (cost.total - cost.dollars)/.25;
	cost.dimes = (cost.total - cost.dollars - cost.quarters*.25)/.1;
	cost.nickels = (cost.total - cost.dollars - cost.quarters*.25 - cost.dimes*.1)/.05;
	cost.pennies = (cost.total)/.01;


	printf("The total cost is %.2f\n", cost.total);
	printf("%d dollars\n", cost.dollars);
	printf("%d quarters\n", cost.quarters);
	printf("%d dimes\n", cost.dimes);
	printf("%d nickels\n", cost.nickels);
	printf("%d pennies\n", cost.pennies);
	 
}

```

Using fixed-point arithmetic instead of floating-point for financial computations is a good idea, but if you do choose to use floating-point, all you need in this case is to use the function 'round':

```
	cost.pennies = round((cost.total)/.01);
```

---

