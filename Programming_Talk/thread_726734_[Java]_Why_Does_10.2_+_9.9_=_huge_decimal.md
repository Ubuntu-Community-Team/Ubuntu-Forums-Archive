---
title: "[Java] Why Does 10.2 + 9.9 = huge decimal?"
date: 2008-03-17
forum: Programming Talk
---

### Post by TreeFinger on 2008-03-17
Running the following code:

```

	float number1, number2, sum, diff, product;
		Scanner inputIntegers = new Scanner(System.in);
		
		System.out.println("Enter 2 decimal point numbers; each followed by enter:");
		number1 = inputIntegers.nextFloat();
		number2 = inputIntegers.nextFloat();
		sum = number1 + number2;
		diff = number1 - number2;
		product = number1 * number2;
		
		System.out.println("Sum: " + sum);
		System.out.println("Difference: " + diff);
		System.out.println("Product: " + product);
	}

```

with first input of: 10.2
second input of: 9.9

gives me this output:
Sum: 20.099998
Difference: 0.3000002
Product: 100.979996

Why? Other numbers are producing the same type of output. While others are not.

---

### Post by lnostdal on 2008-03-17
[http://docs.sun.com/source/806-3568/ncg_goldberg.html](http://docs.sun.com/source/806-3568/ncg_goldberg.html)

---

### Post by TreeFinger on 2008-03-17
> **lnostdal said:**
> [http://docs.sun.com/source/806-3568/ncg_goldberg.html](http://docs.sun.com/source/806-3568/ncg_goldberg.html)

Would you be able to tell me if I am doing something wrong? The problem asks for two floating point numbers to be used. I read the previous chapters and I don't see anything about this happening.

---

### Post by jespdj on 2008-03-17
The point of lnostdal's link is this:

Floating-point numbers in Java, like in many other programming languages, are represented using the [IEEE 754](http://en.wikipedia.org/wiki/IEEE_754-1985) standard. Floating-point numbers in computers are not infinitely precise. Rounding errors happen when you do calculations with floating-point numbers.

Not all numbers can be accurately stored using the IEEE 754 floating-point format. You happen to be using some numbers that can't be accurately stored.

One solution is to format the number you're printing to the screen with a limited number of decimals:
[php]
System.out.printf("Sum: %.3f%n", sum);
System.out.printf("Difference: %.3f%n", diff);
System.out.printf("Product: %.3f%n", product);
[/php]

---

