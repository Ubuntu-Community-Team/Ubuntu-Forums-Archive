---
title: "[Java] loops with accumlators"
date: 2009-02-18
forum: Programming Talk
---

### Post by gotenks05 on 2009-02-18
I am having troubles with another program for a programming class.  I need to make a program that doubles the previous number depending on the number of days the user types in.  I've got it to compile and I know errors at runtime are not the same as syntax errors.  It terminates before starting the second loop.  What do I need to do to fix this?

the program code looks like this:

```
import java.util.*;

public class Pennies
{
	public static void main(String[] args)
	{

		double pay = 1;  // pennies
		int days;  //  number of days;
		double today;

		Scanner keyboard = new Scanner(System.in);
		double Total = 0.0;

		System.out.print("Enter the number of days worked:  ");

		days = keyboard.nextInt();

		while (days < 1)
		{
			System.out.println("Invalid input please Enter a new number.");
		days = keyboard.nextInt();
		}

		for (int count = 1; count <= days; count++)
		{
			today = pay * 2;
			Total += today;
		}
		
	}
}
```

---

### Post by Reiger on 2009-02-18
Hint: exactly what happens should nextInt() return a value less than 1? Or: don't blindly assume that all IO works as expected.

---

### Post by HotCupOfJava on 2009-02-18
Do you output the results?

---

### Post by gotenks05 on 2009-02-18
> **Reiger said:**
> Hint: exactly what happens should nextInt() return a value less than 1? Or: don't blindly assume that all IO works as expected.

This is not opening a file, so IO exceptions are not needed.  I don't have the java.io package imported anyway.  It is kind of obvious.  The while loop takes effect, if the value is less than one.

> **HotCupOfJava said:**
> Do you output the results?

I guess I did forget that I'll try it.

Update:  I got it to go further, but now I can't get it to do the other half.  The math is correct, but I don't get the previous number doubled.  So far, so far it is the same number being multiplied by two.  Do I need to import java.io?

---

### Post by simeon87 on 2009-02-19
The value of pay doesn't change in your program.. so in the last loop, it'll always set today to pay * 2.. which is always the same value. If you want the number to double, you'd need to change pay as well. For example:

```

for (int count = 1; count <= days; count++)
{
    today = pay * 2;
    pay = today;
    Total += today;
}

```

You could even rewrite it so it doesn't use the today and the pay variable.. one variable would be enough because they both seem to serve the same purpose, to store today's pay.

---

### Post by gotenks05 on 2009-02-19
Thanks for the help everyone.

---

