---
title: "Created two basic java programs succesfully but still have a question about them"
date: 2009-09-01
forum: Programming Talk
---

### Post by s3a on 2009-09-01
I've been helped when creating these two programs but I would like to know why it is necessary for me to use the modulus before the division in the first scenario and to use the division after the modulus in the second scenario.

[I]import java.util.Scanner;



public class Assignment_1A_1



{



	public static void main (String [] args)



	{

		Scanner kb;

		kb = new Scanner(System.in);



		System.out.print("How many seconds? ");



		int time_input_in_seconds = kb.nextInt();

		int SECONDS = (time_input_in_seconds % 60);

		int MINUTES = ((time_input_in_seconds /60) % 60);

		int HOURS = ((time_input_in_seconds / 3600) % 24);

		int DAYS = ((time_input_in_seconds / 86400) % 7);



		System.out.println("Days: " + DAYS);

		// Deniz Akcal
// Purpose:System.out.println("Hours: " + HOURS);

		System.out.println("Minutes: " + MINUTES);

		System.out.println("Seconds: " + SECONDS);





	}

}

[/I]

VS

[I]import java.util.Scanner;

public class Assignment_1A_2
{
	public static void main (String [] args)

	{

	Scanner kb;
	kb = new Scanner(System.in);

	System.out.print("How many cents? ");
	int inputed_pennies = kb.nextInt();

	int PENNIES = (inputed_pennies % 5);
	int NICKELS = ((inputed_pennies % 5) / 2);
	int DIMES = ((inputed_pennies % 25) / 10);
	int QUARTERS = (inputed_pennies / 25);

	System.out.println(QUARTERS + " Quarters");
	System.out.println(DIMES + " Dimes");
	System.out.println(NICKELS + " Nickels");
	System.out.println(PENNIES + " Pennies");

	}
}[/I]

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by DaithiF on 2009-09-01
nickels doesn't look right to me (a nickel = 5 cents, right?)

for 19 pennies, wouldn't this would give 0 quarters, 1 dime, 2 nickels, 4 pennies ?  
(i haven't input/run the code, i'm just eyeballing it, so apologies if i'm wrong.)

---

### Post by Arndt on 2009-09-01
> **s3a said:**
> I've been helped when creating these two programs but I would like to know why it is necessary for me to use the modulus before the division in the first scenario and to use the division after the modulus in the second scenario.

[I]import java.util.Scanner;



public class Assignment_1A_1



{



	public static void main (String [] args)



	{

		Scanner kb;

		kb = new Scanner(System.in);



		System.out.print("How many seconds? ");



		int time_input_in_seconds = kb.nextInt();

		int SECONDS = (time_input_in_seconds % 60);

		int MINUTES = ((time_input_in_seconds /60) % 60);

		int HOURS = ((time_input_in_seconds / 3600) % 24);

		int DAYS = ((time_input_in_seconds / 86400) % 7);



		System.out.println("Days: " + DAYS);

		// Deniz Akcal
// Purpose:System.out.println("Hours: " + HOURS);

		System.out.println("Minutes: " + MINUTES);

		System.out.println("Seconds: " + SECONDS);





	}

}

[/I]

VS

[I]import java.util.Scanner;

public class Assignment_1A_2
{
	public static void main (String [] args)

	{

	Scanner kb;
	kb = new Scanner(System.in);

	System.out.print("How many cents? ");
	int inputed_pennies = kb.nextInt();

	int PENNIES = (inputed_pennies % 5);
	int NICKELS = ((inputed_pennies % 5) / 2);
	int DIMES = ((inputed_pennies % 25) / 10);
	int QUARTERS = (inputed_pennies / 25);

	System.out.println(QUARTERS + " Quarters");
	System.out.println(DIMES + " Dimes");
	System.out.println(NICKELS + " Nickels");
	System.out.println(PENNIES + " Pennies");

	}
}[/I]

Any input would be greatly appreciated!
Thanks in advance!

You can do it either way.

---

### Post by mcla0203 on 2009-09-01
If you are worried about precedence of operations and want to make sure its clear, just use parenthesees...  I've been developing with java for a few years now and I do not remember precedence of each operation.  And even if I did know it at the time, I would probably forget eventually... so I'd just put the extra set of parens.. ()    =]

---

### Post by s3a on 2009-09-03
> **Arndt said:**
> You can do it either way.

I tried inverting the % with the / as well as switching their corresponding numbers and it always gives me a result other than what I expect.

---

### Post by fiddler616 on 2009-09-03
In general, it'd be super-fantastic if you used the "[code]" tags for your code. They preserve whitespace, and makes reading things a lot easier.

And to answer your question (and this might be wrong, because the logic of the pennies one just ripped a hole in my mind), it looks like you're using different approaches for the two different programs. You could code #2 in the same way as #1 (or vice versa), but you'd have to change the numbers.

I also think there's a bug in #2, because if you try "17," it'll output 2 pennies, 1 nickel, 0 dimes and 0 quarters. It should be one dime.

---

### Post by Arndt on 2009-09-03
> **s3a said:**
> I tried inverting the % with the / as well as switching their corresponding numbers and it always gives me a result other than what I expect.

I think it helps to think about what the operations do, not just try things.

You can compute the coins in the order quarter, dime, nickel, cent (or whatever it was), or in the order cent, nickel, dime, quarter. Obviously the math needs to be different in the two cases.

---

### Post by Reiger on 2009-09-03
Forgive me if I am too "condescending" but the logic you should adopt is that of converting number systems: the most significant "number" is converted first then the next significant and so on.

E.g. converting 123 in decimal to the equivalent in binary is done by converting 100 to binary, then converting 20 to binary, then converting 3 to binary and finally adding the subtotals:

Thus: (100 = 64 + 32 + 4 = 2^6 + 2^5 + 2^2), (20 = 16 + 4 = 2^4 + 2^2), (3 = 2 + 1 = 2^1 + 2^0)
```

1*10^2 : 1100100
2*10^1 :   10100
3*10^0 :      11
-------------
123    : 1111011

```

As you can see there are common factors which is where you can save time by using division/modulus. This gives you immediately a suitable "Unit Test" (a test to verify correctness of code): check if whatever alternative formula you adopt yields the exact same results as the "reference implementation".

Please note that it is perfectly possible for number systems to not have a proper radix (base) or at least an impractical one: the sequence of Fibonacci numbers also form a number system; as does the sequence of Prime numbers... So yes, your coin system can be modeled as a Number system.

---

