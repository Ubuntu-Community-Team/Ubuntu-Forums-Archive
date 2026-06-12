---
title: "(Java) Error I get when attempting to write to a file"
date: 2010-02-05
forum: Programming Talk
---

### Post by s3a on 2010-02-05
Here are my classes:

```
//import java.io.IOException;
//import java.io.File;
import java.util.Scanner;
import java.io.*;

public class CustomerReport
{


	public static void main(String[] args) throws IOException
	{
		// Prompt user for and read file name
		System.out.print("Enter input file name: ");
		Scanner kb = new Scanner(System.in);
		String filename = kb.next();

		int index = 0;
		BankAccount accounts[] = new BankAccount[60];

		// Create a scanner object and associate it with the input file
		Scanner fileScanner = new Scanner(new File(filename));

		// Read id, balance, and name items from each line and record them
		while(fileScanner.hasNextLine())
		{
			int id = fileScanner.nextInt();
			double balance = fileScanner.nextDouble();
			String name = fileScanner.nextLine();
			
			if(id >= 11000 && id <= 11100 && balance >= 50.0)
			{
				System.out.printf("%5d  %10.2f  %20s\n", id, balance, name);
				accounts[index] = new BankAccount(name, id, balance);
			}
			index++;
		}
		fileScanner.close();
		
		// Prompt the user for and read the name of the error file.
		filename = kb.next();
		
		// Then, Open the error file for writing.
		PrintWriter printWriter = PrintWriter(new File(filename));
		//printWriter.println("Hey");
		//printWriter.close();
	}
}
```

and

```
public class BankAccount

{

	private String name;

	private int accountNumber;

	private double balance;



	public BankAccount(String name, int accountNumber)

	{

		this.name = name;

		this.accountNumber = accountNumber;

		balance = 0.0;

	}

	public BankAccount(String name, int accountNumber, double balance)

	{

		this.name = name;

		this.accountNumber = accountNumber;

		this.balance = balance;

	}

	private void setBalance(double balance)

	{

		this.balance = balance;

	}

	public double getBalance()

	{

		return balance;

	}

	public void setName(String name)

	{

		this.name = name;

	}

	public String getName()

	{

		return name;

	}

	public void setAccountNumber(int accountNumber)

	{

		this.accountNumber = accountNumber;

	}

	public int getAccountNumber()

	{

		return accountNumber;

	}

	public boolean deposit(double amount)

	{

		if(amount >= 0)

		{

			this.balance += amount;

			return true;

		}

		else

			return false;

	}

	public boolean widthdraw(double amount)

	{

		if(amount >= 0 && amount <= balance)

		{

			this.balance -= amount;

			return true;

		}

		else

			return false;

	}

	public String toString() // Check

	{

		String str = "Name: " + name + "\nAccount Number: " + accountNumber + "\nBalance: " + balance;

		return str;

	}

	public boolean equals(Object obj) // Check

	{

		

		if(this == obj)

			return true;



		if(obj == null)

			return false;



		if(this.getClass() != obj.getClass())

			return false;



		boolean result;

		BankAccount bankAccount = (BankAccount)obj;

		

		boolean haveSameName  = this.getName().equals(bankAccount.getName());

		boolean haveSameBalance  = this.getBalance() == bankAccount.getBalance();

		boolean haveSameAccount = this.getAccountNumber() == bankAccount.getAccountNumber();

		if(haveSameName && haveSameBalance && haveSameAccount)

			result = true;

		else

			result = false;

		return result;		

	}

}
```

and here is the input file:

```
11040   593.25   Louis Wilson
11065   6.00     Tjay Kervin
11083   426.00   Nicolas Phillips
11059   3.50     Ken Belanger
11045   711.25   Ahmad Kirk
10132   19.00    John Miller
11043   229.75   Daniel Fraser
11014   320.50   Mario Pappas
11014   864.25   Nicolas Wallner
11085   228.75   Kevin Ward
11071   883.00   Corey Blackhawk
10170   992.50   Luca Kirk
11085   257.50   Nadezda Kervin
11071   630.00   Nicolas Kim
11032   95.50    Deniz Cooke
11054   6.00     Karen Smith
11068   710.50   Ivaylo Wallner
11073   862.50   Ken Nowak
11031   510.25   Ahmad Kirk
11079   410.50   Luca Blackhawk
10132   9.00     Omar Wallner
11084   256.25   Shahrad Wallner
11067   630.50   Joseph Gorski
11080   402.00   karen Yavorov
11065   401.25   Shawn Rowe
11070   277.25   Shahrad Gorski
11088   322.50   Corey Kirk
11043   6.50     David Boucher
11015   509.00   Nicolas Ropiak
11065   932.50   Omar Faraci
10170   864.50   Shahrad Kirk
11072   278.00   Kerry Smith
11015   864.50   Jacob Gorski
11060   3.75     Corey Wallner
11054   327.25   Taimoor Boucher
11038   409.00   Shahrad Fraser
11027   229.00   Nadezda Garrett
11031   382.00   Corey Ward
11087   277.25   Ahmad Blackhawk
11042   408.25   David Smith
```

My error message:
```
javac CustomerReport.java
CustomerReport.java:43: cannot find symbol
symbol  : method PrintWriter(java.io.File)
location: class CustomerReport
		PrintWriter printWriter = PrintWriter(new File(filename));
		                          ^
1 error
```

I really can't see the mistake is so I was hoping someone could point it out to me please.

Any help would be appreciated!
Thanks in advance!

---

### Post by s3a on 2010-02-05
Omg I'm so stupid:

PrintWriter pw = **new** PrintWriter(new File(filename));

was my error.

---

### Post by Reiger on 2010-02-05
The error message says: you attempt to use a method (constructor in this case) that does not exist. There is no method: "PrintWriter(File)".

So it is time to consult Java 101: Methods. How are these identified? By signature. What is a (method) signature in Java? A name and a bunch of type parameters.

If you want to learn Java, you should spend some time learning about these error messages, learning their jargon, and then learning how to interpret them by examining your error message & source code via deduction.

This will help you if you intend to continue using Java because when you start to work with more complex projects the error messages get an order of magnitude more creatively non-descriptive about the apparent problem at hand.

---

