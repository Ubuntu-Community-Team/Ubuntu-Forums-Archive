---
title: "Scanner cannot be called properly?"
date: 2008-07-25
forum: Programming Talk
---

### Post by D.Sync on 2008-07-25
I had import java.util.*; properly but still the error below exist during compilation:

Exception in thread "main" java.util.NoSuchElementException
	at java.util.Scanner.throwFor(Scanner.java:838)
	at java.util.Scanner.next(Scanner.java:1461)
	at java.util.Scanner.nextInt(Scanner.java:2091)
	at java.util.Scanner.nextInt(Scanner.java:2050)
	at Q8.main(Q8.java:32)

Exited: 256

---

### Post by hod139 on 2008-07-25
Can you post the code that is causing the error?

---

### Post by Zugzwang on 2008-07-25
> **D.Sync said:**
> I had import java.util.*; properly but still the error below exist during compilation

It looks like your error (more precisely: exception) appeared at runtime but not during compilation. To see why that exception is thrown, get familiar with a debugger and inspect your program step-by-step.

---

### Post by D.Sync on 2008-07-26
Whenever I import Scanner function with the code below, the error above occured: 
I already installed sun-java-6 jdk and jre via the repository.

> import java.util.*;

public class Q8 {
	public static void main(String[] args) {

	//1. Display input message. Require user the enter a whole number from 1 to 99
	System.out.println("Welcome to 'D.Sync Combination of Coins Machine'!");
	System.out.println("Enter a whole number from 1 to 99.");
	System.out.println("I will find a combination of coins");
	System.out.println("that equals that amount of change.");

	//2. Read the amount
	Scanner input = new Scanner (System.in);

	//3. Storing the original amount
	int originalAmount = input.nextInt();

	//4. Make a copy of the amount. The var amount will be use to calculate the number of
	//    quarters, dimes, nickels and pennies.
	int amount = originalAmount;

		//5. Conditional Check. If the input number is less than 1 or greater than 99
		if (originalAmount <1 || originalAmount >99) {
		System.out.println("Invalid amount!");
		}

		else {

		//6. Find the maximum number of quarters in the amount.
		int quarters = amount / 25;

		//7. Number of dimes, calculation is pretty straightforward from the formula below
		int dimes = (amount % 25) / 10;

		//8. Number of nickels
		int nickels = ((amount % 25) % 10) / 5;

		//9. Number of pennies
		// Method One:
		// int pennies = (((amount % 25) % 10) % 5) / 1;
		// Method Two:
		int pennies = amount % 5;

		//10. Print the original amount and the quantities of each coin.
		System.out.println(originalAmount + " cents in coins can be given as:");

			//11. Checking condition for quarters, if quarter = 1, display as quarter, else, display as quarters
			if (quarters > 0) {
			System.out.println(quarters + " quarters");
			}
			else {
			System.out.println(quarters + " quarter");
			}

			if (dimes > 0) {
			System.out.println(dimes + " dimes");
			}
			else {
			System.out.println(dimes + " dime");
			}

			if (nickels > 0) {
			System.out.println(nickels + " nickels");
			}
			else {
			System.out.println(nickels + " nickle");
			}

			if (pennies > 0) {
			System.out.println(pennies + " pennies");
			}

			else {
			System.out.println(pennies + " penny");
			}
		}
	}
}

---

### Post by ceclauson on 2008-07-26
I tried running your code in Netbeans, and it ran fine on my system.

Are you using the Sun JRE?  Ubuntu comes with gij (GNU bytecode Interpreter for Java) by default as the Java runtime.  It's a free, open-source alternative to Sun's Java runtime, but it's not a complete implementation, so platform calls tend to fail with cryptic error messages.

In order to find out, try going to /usr/bin, find the file called java, and see if it's really a symbolic link to gij.  This is how Ubuntu comes by default, and means you're using the GNU runtime.  If this is the case, and you'll want to get Sun Java, [this]("https://help.ubuntu.com/community/Java") page should help.

Hope this was helpful,
Cooper

---

