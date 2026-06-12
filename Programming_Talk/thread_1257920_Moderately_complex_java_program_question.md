---
title: "Moderately complex java program question"
date: 2009-09-04
forum: Programming Talk
---

### Post by s3a on 2009-09-04
import java.util.Scanner;

public class PQ

{

	public static void main (String [] args)

	{

		Scanner kb;

		kb = new Scanner(System.in);

	System.out.print("Enter your savings from the first week: ");

		int quarters = kb.nextInt();
		int dimes = kb.nextInt();
		int nickels = kb.nextInt();
		int pennies = kb.nextInt();

	System.out.print("Enter your savings from the second week: ");

		int quarters2 = kb.nextInt();
		int dimes2 = kb.nextInt();
		int nickels2 = kb.nextInt();
		int pennies2 = kb.nextInt();

	System.out.print("Enter your savings from the third week: ");

		int quarters3 = kb.nextInt();
		int dimes3 = kb.nextInt();
		int nickels3 = kb.nextInt();
		int pennies3 = kb.nextInt();

	System.out.print("Enter your savings from the fourth week: ");

		int quarters4 = kb.nextInt();
		int dimes4 = kb.nextInt();
		int nickels4 = kb.nextInt();
		int pennies4 = kb.nextInt();

		System.out.println();

		int quarters_4weeks = quarters + quarters2 + quarters3 + quarters4;
		int dimes_4weeks = dimes + dimes2 + dimes3 + dimes4;
		int nickels_4weeks = nickels + nickels2 + nickels3 + nickels4;
		int pennies_4weeks = pennies + pennies2 + pennies3 + pennies4;

	// Four weeks savings:

	System.out.print("------------------------");
	System.out.println();
	System.out.println("Your four weeks savings: ");
	System.out.print("------------------------");
	System.out.println();


	System.out.println("Quarters: " + quarters_4weeks);
	System.out.println("Dimes: " + dimes_4weeks);
	System.out.println("Nickelss: " + nickels_4weeks);
	System.out.println("Pennies: " + pennies_4weeks);
	System.out.println();



//double  weeklyAverage = ((quarters_4weeks * 25.0) + (dimes_4weeks * 10.0) + (nickels_4weeks * 5.0) + (pennies_4weeks)) / 400.0;

**double  weeklyAverage = ((quarters_4weeks * 0.25) + (dimes_4weeks * 0.1) + (nickels_4weeks * 0.05) + (pennies_4weeks * 0.01)) / 4.0;**

	System.out.println("Weekly average: ");
	System.out.println();
	System.out.println("$" + weeklyAverage);
	System.out.println();

	System.out.println("Thank you for using my program!");
	System.out.println();

	}

}

VS

import java.util.Scanner;

public class PQ

{

	public static void main (String [] args)

	{

		Scanner kb;

		kb = new Scanner(System.in);

	System.out.print("Enter your savings from the first week: ");

		int quarters = kb.nextInt();
		int dimes = kb.nextInt();
		int nickels = kb.nextInt();
		int pennies = kb.nextInt();

	System.out.print("Enter your savings from the second week: ");

		int quarters2 = kb.nextInt();
		int dimes2 = kb.nextInt();
		int nickels2 = kb.nextInt();
		int pennies2 = kb.nextInt();

	System.out.print("Enter your savings from the third week: ");

		int quarters3 = kb.nextInt();
		int dimes3 = kb.nextInt();
		int nickels3 = kb.nextInt();
		int pennies3 = kb.nextInt();

	System.out.print("Enter your savings from the fourth week: ");

		int quarters4 = kb.nextInt();
		int dimes4 = kb.nextInt();
		int nickels4 = kb.nextInt();
		int pennies4 = kb.nextInt();

		System.out.println();

		int quarters_4weeks = quarters + quarters2 + quarters3 + quarters4;
		int dimes_4weeks = dimes + dimes2 + dimes3 + dimes4;
		int nickels_4weeks = nickels + nickels2 + nickels3 + nickels4;
		int pennies_4weeks = pennies + pennies2 + pennies3 + pennies4;

	// Four weeks savings:

	System.out.print("------------------------");
	System.out.println();
	System.out.println("Your four weeks savings: ");
	System.out.print("------------------------");
	System.out.println();


	System.out.println("Quarters: " + quarters_4weeks);
	System.out.println("Dimes: " + dimes_4weeks);
	System.out.println("Nickelss: " + nickels_4weeks);
	System.out.println("Pennies: " + pennies_4weeks);
	System.out.println();



**double  weeklyAverage = ((quarters_4weeks * 25.0) + (dimes_4weeks * 10.0) + (nickels_4weeks * 5.0) + (pennies_4weeks)) / 400.0;**

//double  weeklyAverage = ((quarters_4weeks * 0.25) + (dimes_4weeks * 0.1) + (nickels_4weeks * 0.05) + (pennies_4weeks * 0.01)) / 4.0;

	System.out.println("Weekly average: ");
	System.out.println();
	System.out.println("$" + weeklyAverage);
	System.out.println();

	System.out.println("Thank you for using my program!");
	System.out.println();

	}

}

_Input:_
1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4

_Output:_
Weekly average: $0.6400000000000001

VS

Weekly average: $0.64

What is going on?!

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2009-09-04
> 
double weeklyAverage = ((quarters_4weeks * 25.0) + (dimes_4weeks * 10.0) + (nickels_4weeks * 5.0) + (pennies_4weeks)) / 400.0;

Did you mean to divide by 100.0??

And with respect to outputting the data:
```

import java.text.NumberFormat;

...

NumberFormat numFmt = NumberFormat.getCurrencyInstance();
System.out.println(numFmt.format(weeklyAverage));

...

```

---

### Post by stroyan on 2009-09-04
The java double type is a 64 bit floating point number using IEEE standard types.
[http://en.wikipedia.org/wiki/IEEE_754-2008]("http://en.wikipedia.org/wiki/IEEE_754-2008")
The representation is actually a binary number with 53 bits of precision and a binary exponent.
Using a decimal constant or printing a double involves conversion between decimal and binary representations.
That means that decimal fractions cannot be exactly represented.
When you work with summing numbers that are 100 times as large you are actually using different approximations of those values.
You might get results more like you expect using the BigDecimal type as discussed here-
[http://www.javaworld.com/javaworld/jw-06-2001/jw-0601-cents.html]("http://www.javaworld.com/javaworld/jw-06-2001/jw-0601-cents.html")
But even the BigDecimal type will require specific rounding decisions if you will be doing imprecise math such as dividing dollar and cents amounts by "3".

---

### Post by Arndt on 2009-09-04
> **s3a said:**
> import java.util.Scanner;

public class PQ

{

	public static void main (String [] args)

	{

		Scanner kb;

		kb = new Scanner(System.in);

	System.out.print("Enter your savings from the first week: ");

		int quarters = kb.nextInt();
		int dimes = kb.nextInt();
		int nickels = kb.nextInt();
		int pennies = kb.nextInt();

	System.out.print("Enter your savings from the second week: ");

		int quarters2 = kb.nextInt();
		int dimes2 = kb.nextInt();
		int nickels2 = kb.nextInt();
		int pennies2 = kb.nextInt();

	System.out.print("Enter your savings from the third week: ");

		int quarters3 = kb.nextInt();
		int dimes3 = kb.nextInt();
		int nickels3 = kb.nextInt();
		int pennies3 = kb.nextInt();

	System.out.print("Enter your savings from the fourth week: ");

		int quarters4 = kb.nextInt();
		int dimes4 = kb.nextInt();
		int nickels4 = kb.nextInt();
		int pennies4 = kb.nextInt();

		System.out.println();

		int quarters_4weeks = quarters + quarters2 + quarters3 + quarters4;
		int dimes_4weeks = dimes + dimes2 + dimes3 + dimes4;
		int nickels_4weeks = nickels + nickels2 + nickels3 + nickels4;
		int pennies_4weeks = pennies + pennies2 + pennies3 + pennies4;

	// Four weeks savings:

	System.out.print("------------------------");
	System.out.println();
	System.out.println("Your four weeks savings: ");
	System.out.print("------------------------");
	System.out.println();


	System.out.println("Quarters: " + quarters_4weeks);
	System.out.println("Dimes: " + dimes_4weeks);
	System.out.println("Nickelss: " + nickels_4weeks);
	System.out.println("Pennies: " + pennies_4weeks);
	System.out.println();



//double  weeklyAverage = ((quarters_4weeks * 25.0) + (dimes_4weeks * 10.0) + (nickels_4weeks * 5.0) + (pennies_4weeks)) / 400.0;

**double  weeklyAverage = ((quarters_4weeks * 0.25) + (dimes_4weeks * 0.1) + (nickels_4weeks * 0.05) + (pennies_4weeks * 0.01)) / 4.0;**

	System.out.println("Weekly average: ");
	System.out.println();
	System.out.println("$" + weeklyAverage);
	System.out.println();

	System.out.println("Thank you for using my program!");
	System.out.println();

	}

}

VS

import java.util.Scanner;

public class PQ

{

	public static void main (String [] args)

	{

		Scanner kb;

		kb = new Scanner(System.in);

	System.out.print("Enter your savings from the first week: ");

		int quarters = kb.nextInt();
		int dimes = kb.nextInt();
		int nickels = kb.nextInt();
		int pennies = kb.nextInt();

	System.out.print("Enter your savings from the second week: ");

		int quarters2 = kb.nextInt();
		int dimes2 = kb.nextInt();
		int nickels2 = kb.nextInt();
		int pennies2 = kb.nextInt();

	System.out.print("Enter your savings from the third week: ");

		int quarters3 = kb.nextInt();
		int dimes3 = kb.nextInt();
		int nickels3 = kb.nextInt();
		int pennies3 = kb.nextInt();

	System.out.print("Enter your savings from the fourth week: ");

		int quarters4 = kb.nextInt();
		int dimes4 = kb.nextInt();
		int nickels4 = kb.nextInt();
		int pennies4 = kb.nextInt();

		System.out.println();

		int quarters_4weeks = quarters + quarters2 + quarters3 + quarters4;
		int dimes_4weeks = dimes + dimes2 + dimes3 + dimes4;
		int nickels_4weeks = nickels + nickels2 + nickels3 + nickels4;
		int pennies_4weeks = pennies + pennies2 + pennies3 + pennies4;

	// Four weeks savings:

	System.out.print("------------------------");
	System.out.println();
	System.out.println("Your four weeks savings: ");
	System.out.print("------------------------");
	System.out.println();


	System.out.println("Quarters: " + quarters_4weeks);
	System.out.println("Dimes: " + dimes_4weeks);
	System.out.println("Nickelss: " + nickels_4weeks);
	System.out.println("Pennies: " + pennies_4weeks);
	System.out.println();



**double  weeklyAverage = ((quarters_4weeks * 25.0) + (dimes_4weeks * 10.0) + (nickels_4weeks * 5.0) + (pennies_4weeks)) / 400.0;**

//double  weeklyAverage = ((quarters_4weeks * 0.25) + (dimes_4weeks * 0.1) + (nickels_4weeks * 0.05) + (pennies_4weeks * 0.01)) / 4.0;

	System.out.println("Weekly average: ");
	System.out.println();
	System.out.println("$" + weeklyAverage);
	System.out.println();

	System.out.println("Thank you for using my program!");
	System.out.println();

	}

}

_Input:_
1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4

_Output:_
Weekly average: $0.6400000000000001

VS

Weekly average: $0.64

What is going on?!

Any input would be greatly appreciated!
Thanks in advance!

Are you asking why the number ends in 000001? It's because most numbers with a limited number of decimals cannot be represented exactly by a binary computer. You can format the number when outputting it so only two decimals (or three, or something) are shown.

---

### Post by s3a on 2009-09-05
Yes that is what I'm asking but how come the second output doesn't show all those decimals and the first one does (The math looks the same to me)?

(Dividing by 400 means /4 for average then /100 for unit conversion from cents to dollars so /(4*100). I do realize I should make code more readable for others to work with. I will make things more clear in the future.)

---

### Post by Ruhe on 2009-09-05
[What Every Computer Scientist Should Know About Floating-Point Arithmetic]("http://www.physics.ohio-state.edu/~dws/grouplinks/floating_point_math.pdf")


Need correct precision? Use [BigDecimal]("http://www.j2ee.me/javase/6/docs/api/java/math/BigDecimal.html").

---

### Post by dwhitney67 on 2009-09-05
BigDecimal is wonderful, but since the assignment deals with currency, the NumberFormat should be considered.  The NumberFormat takes care of the precision for the (local) currency, and provides the currency symbol.

Here's a knockoff of the OP's code:
```

import java.util.Scanner;
import java.text.NumberFormat;

public class WeeklyAverage
{
   public static void main(String[] args)
   {
      Scanner kb = new Scanner(System.in);

      int quarters = 0;
      int dimes    = 0;
      int nickels  = 0;
      int pennies  = 0;

      for (int week = 1; week <= 4; ++week)
      {
         System.out.print("Enter number of quarters, dimes, nickels, and pennies in savings for week " + week + " [ex. 1 3 2 5]: ");

         quarters += kb.nextInt();
         dimes    += kb.nextInt();
         nickels  += kb.nextInt();
         pennies  += kb.nextInt();
      }

      double savings   = (quarters * 0.25) + (dimes * 0.10) + (nickels * 0.05) + (pennies * 0.01);
      double weeklyAvg = savings / 4;

      NumberFormat numFmt = NumberFormat.getCurrencyInstance();

      System.out.println("\nYour four weeks of savings amounted to: " + numFmt.format(savings));
      System.out.println("Your weekly average of savings were   : " + numFmt.format(weeklyAvg));
   }
}

```

---

### Post by Ruhe on 2009-09-05
From every java programer's bible "Effective Java Programming 2":
**Item 48: Avoid float and double if exact answers are required.**

Did you test your code?

```

        int quarters = 1;
        int dimes = 4;
        int nickels = 10;
        int pennies = 15;

        double savings = (quarters * 0.25) + (dimes * 0.10) + (nickels * 0.05) + (pennies * 0.01);
        double weeklyAvg = savings / 4;

        System.out.println(weeklyAvg); // **prints 0.32499999999999996**

```

Now imagine what could happen if you used such code in the real banking program :)

---

