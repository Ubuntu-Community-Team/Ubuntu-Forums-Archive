---
title: "(Java) No syntax errors but Java says &quot;java.lang.NullPointerException&quot;"
date: 2010-02-08
forum: Programming Talk
---

### Post by s3a on 2010-02-08
I put in bold what I think is the cause of the error since eclipse (my IDE) had said "The method setAccountNumber(int) is undefined for the type CustomerReport" before I added the "accounts[index]." part. When I running, I get "Exception in thread "main" java.lang.NullPointerException
	at CustomerReport.main(CustomerReport.java:41)."

Here is my CustomerReport class:
```
//import java.io.IOException;
//import java.io.File;
import java.util.Scanner;
import java.io.*;

public class CustomerReport
{
   public static void main(String[] args) throws IOException
   {
      // Initialize sumBalance variable
	  double sumBalance = 0.0;
	  // Prompt user for and read file name
      System.out.print("Enter input file name: ");
      Scanner kb = new Scanner(System.in);
      String[] filename = new String[3];
      
      filename[0] = kb.next();

      int index = 0;
      BankAccount accounts[] = new BankAccount[60];

      // Create a scanner object and associate it with the input file
      Scanner fileReader = new Scanner(new File(filename[0]));

      // Prompt the user for and read the name of the error file.
      System.out.print("\nEnter the name of the error file to be written: ");
      filename[1] = kb.next();
      // Open the error file for writing.
      PrintWriter errorWrite = new PrintWriter(new File(filename[1]));
      
      // Prompt the user for and read the name of the report file.
      System.out.print("Enter the name of the report file for writing: ");
      filename[2] = kb.next();
      // Open the report file for writing.
      PrintWriter reportWrite = new PrintWriter(new File(filename[2]));
      
      // Read id, balance, and name items from each line and store them in a bank account if it is valid (Check program and comment!!!)
      while(fileReader.hasNextLine() && index < accounts.length)
      {
         int id = fileReader.nextInt();       
         **accounts[index].setAccountNumber(id); // (=Line 41) Added this to get java.lang.NullPointerException problem to go away from what I think is caused by line 52**
         double balance = fileReader.nextDouble();
         String name = fileReader.nextLine();
         
         if(id >= 11000 && id <= 11100 && balance >= 50.0)
         {
            System.out.printf("%5d  %10.2f  %20s\n", id, balance, name);
            accounts[index] = new BankAccount(name, id, balance);
            
            for(int count = 1; count < (accounts.length) - 1; count++)//PART (BELOW) FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!
            {
	            **if( (accounts[index].equals(accounts[count]) && index != count) ||/*(Line 52)*/ (accounts[index].getAccountNumber() == accounts[count].getAccountNumber()) )**
	            {
	            	errorWrite.printf("Invalid input on line #: %5d  %10.2f  %20s\n", accounts[count].getAccountNumber(), accounts[count].getBalance(), accounts[count].getName());
	            	if(accounts[index].getAccountNumber() == accounts[count].getAccountNumber())
	            		errorWrite.println("Duplicated account number");
	            }
	            else if(index != count)
	            {
	            	reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);	            	
	            }
            }//PART (ABOVE) FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!
            sumBalance += accounts[index].getBalance();
            index++;
         }
         else
         {           
        	 errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
        	 if(balance < 50)
         		errorWrite.println("Account balance must be at least 50.0");
         	 if(id < 11000 || id > 11100)
         		 errorWrite.println("Account Number must be in");
         }
        
      }
      // Write the sum of the balances to the file
      reportWrite.println("Sum of balances: " + sumBalance);
                  
      // Close the files:
      fileReader.close();
      errorWrite.close();
      reportWrite.close();
      
   }
}
```

Here is my BankAccount class:
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

And, here is my customers.txt file (aka input file):

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

Can someone point out my mistake please?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2010-02-08
I think I see the problem:
```

BankAccount accounts[] = new BankAccount[60];

```
This allocates 60 handles (ie pointers) to *potential* BankAccount objects, but it does not allocate the actual BankAccount objects themselves.

After you have successfully read in the three pieces of data (id, balance, and name) that fit your criteria, then allocate a BankAccount object in which to store the data.  Something like:
```

BankAccount accounts[] = new BankAccount[60];

...

while (...)
{
   // read data

   if data good
   {
      accounts[index] = new BankAccount(name, acctNum, balance);

      ...
   }
}

```
I did not fully understand what you were trying to weed-out; was it duplicate accounts?  Either way, the above should work.  If you find a unique account, increment index; otherwise reuse the same slot and this will cause the garbage-collector to free the duplicate BankAccount object at a later time.

---

### Post by s3a on 2010-02-08
Actually here is my new CustomerReport class:

```
//import java.io.IOException;
//import java.io.File;
import java.util.Scanner;
import java.io.*;

public class CustomerReport
{
   public static void main(String[] args) throws IOException
   {
      // Initialize sumBalance variable
	  double sumBalance = 0.0;
	  // Prompt user for and read file name
      System.out.print("Enter input file name: ");
      Scanner kb = new Scanner(System.in);
      String[] filename = new String[3];
      
      filename[0] = kb.next();

      int index = 0;
      BankAccount accounts[] = new BankAccount[60];

      // Create a scanner object and associate it with the input file
      Scanner fileReader = new Scanner(new File(filename[0]));

      // Prompt the user for and read the name of the error file.
      System.out.print("\nEnter the name of the error file to be written: ");
      filename[1] = kb.next();
      // Open the error file for writing.
      PrintWriter errorWrite = new PrintWriter(new File(filename[1]));
      
      // Prompt the user for and read the name of the report file.
      System.out.print("Enter the name of the report file for writing: ");
      filename[2] = kb.next();
      // Open the report file for writing.
      PrintWriter reportWrite = new PrintWriter(new File(filename[2]));
      
      // Read id, balance, and name items from each line and store them in a bank account if it is valid (Check program and comment!!!)
      while(fileReader.hasNextLine() && index < accounts.length)
      {
         int id = fileReader.nextInt();       
         **//accounts[index].setAccountNumber(id);** // (=Line 41) Added this to get java.lang.NullPointerException problem to go away from what I think is caused by line 52
         double balance = fileReader.nextDouble();
         String name = fileReader.nextLine();
         
         if(id >= 11000 && id <= 11100 && balance >= 50.0)
         {
            System.out.printf("%5d  %10.2f  %20s\n", id, balance, name);            
            
            for(int count = 1; count < (accounts.length) - 1; count++)//PART (BELOW) FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!
            {
	            if( (accounts[index].equals(accounts[count]) && index != count) ||/*(Line 52)*/ (accounts[index].getAccountNumber() == accounts[count].getAccountNumber()) )
	            {
	            	errorWrite.printf("Invalid input on line #: %5d  %10.2f  %20s\n", accounts[count].getAccountNumber(), accounts[count].getBalance(), accounts[count].getName());
	            	if(accounts[index].getAccountNumber() == accounts[count].getAccountNumber())
	            		errorWrite.println("Duplicated account number");
	            }
	            else if(index != count)
	            {
	            	**accounts[index] = new BankAccount(name, id, balance);**
	            	reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);	            	
	            }
            }//PART (ABOVE) FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!
            sumBalance += accounts[index].getBalance();
            index++;
         }
         else
         {           
        	 errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
        	 if(balance < 50)
         		errorWrite.println("Account balance must be at least 50.0");
         	 if(id < 11000 || id > 11100)
         		 errorWrite.println("Account Number must be in");
         }
        
      }
      // Write the sum of the balances to the file
      reportWrite.println("Sum of balances: " + sumBalance);
                  
      // Close the files:
      fileReader.close();
      errorWrite.close();
      reportWrite.close();
      
   }
}
```

The second bold line shows that I have what you told me to add (unless I misunderstood you). I realized that I do not need the setAccountNumber() method having looked at my code again since the account number is already being dumped to the constructor (second bold line). To answer your question, I want to reject duplicate acounts, in the sense of duplicate everything or duplicate account number.

By the way, I did change the location of the currently second bold line because my previous code created a new account for the duplicate and spent a component of my accounts[] array.

However, I still get the same issue:

> Enter input file name: customers.txt

Enter the name of the error file to be written: err.txt
Enter the name of the report file for writing: out.txt
11040      593.25          Louis Wilson
Exception in thread "main" java.lang.NullPointerException
	at CustomerReport.main(CustomerReport.java:51)

Do you know what's causing this?

---

### Post by abhishek.malhotra35 on 2010-02-08
There are 2 issues with your program. First is the 
BankAccount accounts[] = new BankAccount[60];
Here you have created an array of BankAccount but the array variables are null. So in line 46, when you try to access the variable on that index, it throws error. 

2nd issue comes after I commented line 46. On line 52
if( (accounts[index].equals(accounts[count])
Here here you have only added one BankAccount in accounts array, i.e. at index 0. Your count loop starts with 1. While doing above check, variable in array at index 0 is compared to variable at index 1. Since index 1 is null, null pointer exception is thrown.

---

### Post by dwhitney67 on 2010-02-08
> **abhishek.malhotra35 said:**
> There are 2 issues with your program. First is the 
BankAccount accounts[] = new BankAccount[60];
Here you have created an array of BankAccount but the array variables are null. So in line 46, when you try to access the variable on that index, it throws error. 

2nd issue comes after I commented line 46. On line 52
if( (accounts[index].equals(accounts[count])
Here here you have only added one BankAccount in accounts array, i.e. at index 0. Your count loop starts with 1. While doing above check, variable in array at index 0 is compared to variable at index 1. Since index 1 is null, null pointer exception is thrown.
+2

Thanks for saving me the time of replying to the OP.

---

### Post by Some Penguin on 2010-02-09
> **s3a said:**
> Actually here is my new CustomerReport class:

```
//import java.io.IOException;
//import java.io.File;
import java.util.Scanner;
import java.io.*;

public class CustomerReport
{
   public static void main(String[] args) throws IOException
   {
      // Initialize sumBalance variable
      double sumBalance = 0.0;
      // Prompt user for and read file name
      System.out.print("Enter input file name: ");
      Scanner kb = new Scanner(System.in);
      String[] filename = new String[3];
      
      filename[0] = kb.next();

      int index = 0;
      BankAccount accounts[] = new BankAccount[60];

```

The accounts declaration looks wrong to me -- as in, incorrect syntax.  Are you re-typing code instead of copying and pasting?


> ```

      // Create a scanner object and associate it with the input file
      Scanner fileReader = new Scanner(new File(filename[0]));

      // Prompt the user for and read the name of the error file.
      System.out.print("\nEnter the name of the error file to be written: ");
      filename[1] = kb.next();
      // Open the error file for writing.
      PrintWriter errorWrite = new PrintWriter(new File(filename[1]));
      
      // Prompt the user for and read the name of the report file.
      System.out.print("Enter the name of the report file for writing: ");
      filename[2] = kb.next();
      // Open the report file for writing.
      PrintWriter reportWrite = new PrintWriter(new File(filename[2]));
      
      // Read id, balance, and name items from each line and store them in a bank account if it is valid (Check program and comment!!!)
      while(fileReader.hasNextLine() && index < accounts.length)

```Note:  accounts.length is always 60.

> ```

      {
         int id = fileReader.nextInt();       
         **//accounts[index].setAccountNumber(id);** // (=Line 41) Added this to get java.lang.NullPointerException problem to go away from what I think is caused by line 52

```Boom.  accounts[index] is null, because you didn't create any BankAccount objects.  You created an array that can hold references to them, but didn't populate it.  You then treat the null as a BankAccount, run a method on it, and of course it dies.  

You need to read up on references and arrays.

> ```

         double balance = fileReader.nextDouble();
         String name = fileReader.nextLine();
         
         if(id >= 11000 && id <= 11100 && balance >= 50.0)
         {
            System.out.printf("%5d  %10.2f  %20s\n", id, balance, name);            
            
            for(int count = 1; count < (accounts.length) - 1; count++)//PART (BELOW) FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!

```Skipping account #0 and account #59?  You're also going to explode repeatedly here; even on the first account (#0), you're poking at 1..58, which don't exist.

```
> 
            {
                if( (accounts[index].equals(accounts[count]) && index != count) ||/*(Line 52)*/ (accounts[index].getAccountNumber() == accounts[count].getAccountNumber()) )
                {
                    errorWrite.printf("Invalid input on line #: %5d  %10.2f  %20s\n", accounts[count].getAccountNumber(), accounts[count].getBalance(), accounts[count].getName());
                    if(accounts[index].getAccountNumber() == accounts[count].getAccountNumber())
                        errorWrite.println("Duplicated account number");
                }
                else if(index != count)
                {
                    **accounts[index] = new BankAccount(name, id, balance);**
                    reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);                    
                }
            }//PART (ABOVE) FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!
            sumBalance += accounts[index].getBalance();
            index++;

```
You increment index, even if you didn't create an account?  You really need to think about what index means to you.

```
> 
         }
         else
         {           
             errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
             if(balance < 50)
                 errorWrite.println("Account balance must be at least 50.0");
              if(id < 11000 || id > 11100)
                  errorWrite.println("Account Number must be in");
         }
        
      }
      // Write the sum of the balances to the file
      reportWrite.println("Sum of balances: " + sumBalance);
                  
      // Close the files:
      fileReader.close();
      errorWrite.close();
      reportWrite.close();
      
   }
}
```


You should also have a look at the Collections Framework.  I think a Map might be of use to you.

---

### Post by s3a on 2010-02-09
I modified my code so unless I am making another mistake, it no longer uses null arrays. However, when I attempt to have all valid accounts printed on an output file, it does not print any accounts at all. It doesn't calculate the sum of all the balances of the valid accounts either!

Here is my code:
```
import java.util.Scanner;
import java.io.*;

public class CustomerReport
{
   public static void main(String[] args) throws IOException
   {
      // Initialize sumBalance variable
	  double sumBalance = 0.0;
	  // Prompt user for and read file name
      System.out.print("Enter input file name: ");
      Scanner kb = new Scanner(System.in);
      String[] filename = new String[3];
      
      filename[0] = kb.next();

      
      BankAccount accounts[] = new BankAccount[60];

      // Create a scanner object and associate it with the input file
      Scanner fileReader = new Scanner(new File(filename[0]));

      // Prompt the user for and read the name of the error file.
      System.out.print("\nEnter the name of the error file to be written: ");
      filename[1] = kb.next();
      // Open the error file for writing.
      PrintWriter errorWrite = new PrintWriter(new File(filename[1]));
      
      // Prompt the user for and read the name of the report file.
      System.out.print("Enter the name of the report file for writing: ");
      filename[2] = kb.next();
      // Open the report file for writing.
      PrintWriter reportWrite = new PrintWriter(new File(filename[2]));
      
      // Read id, balance, and name items from each line and store them in a bank account if it is valid (Check program and comment!!!)
      int index = 0;
      while(fileReader.hasNextLine() && index < accounts.length)
      {
         int id = fileReader.nextInt();
         double balance = fileReader.nextDouble();
         String name = fileReader.nextLine();         
         
         if(id >= 11000 && id <= 11100 && balance >= 50.0)
         {
        	boolean isDuplicate = false;
        	System.out.printf("%5d  %10.2f  %20s\n", id, balance, name); // This line assumes no duplicates, therefore it is temporary.
            for(int count = 0; count < index; count++)
            {
	            if(id == accounts[count].getAccountNumber())            
	            {
	            	isDuplicate = true;
	            	errorWrite.printf("Invalid input on line #: %5d  %10.2f  %20s\n", accounts[count].getAccountNumber(), accounts[count].getBalance(), accounts[count].getName());
	            	if(accounts[index].getAccountNumber() == accounts[count].getAccountNumber())
	            		errorWrite.println("Duplicated account number");
	            }
	            else // Check if this is necessary (Right now I think that it is)
	            	isDuplicate = false;
            
            	// Check to see if it is a duplicate. If not, create the account, add its balance to the total balance, write it to the output file then increment index.
	            if(isDuplicate)
	            {
	            	accounts[index] = new BankAccount(name, id, balance);
	            	sumBalance += accounts[index].getBalance();
	            	reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);	            	
	            	index++;
	            }
            }
         }
         else
         {           
        	 errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
        	 if(balance < 50)
         		errorWrite.println("Account balance must be at least 50.0 ");
         	 if(id < 11000 || id > 11100)
         		 errorWrite.println("Account Number must be between 11000 and 11100. ");
         }
      }
      // Write the sum of the balances to the file
      reportWrite.println("Sum of balances: " + sumBalance);
                  
      // Close the files:
      fileReader.close();
      errorWrite.close();
      reportWrite.close();
      
   }
}
```

I've had two classmates read my code and they also had trouble spotting the problem (on this version of my code) :(. What am I doing wrong this time?

---

### Post by dwhitney67 on 2010-02-09
Well, aside from doing things the hard way... um, let's see.

For starters, the conditional in this for-loop will never be true, and because of such, the variable 'index' will never be incremented.
```

for(int count = 0; count < index; count++)

```
Aside from that issue, you have another; compare your comment with the actual:
```

// Check to see if it is a duplicate. If not, create the account, add its balance to the total balance, write it to the output file then increment index.
   if(isDuplicate)

```
Here you seem to want to create a new entry if it is a duplicate.  Huh?  Well, if it is unique (ie not a duplicate), then once again you prevent 'index' from being incremented.

Lastly, I should mention that your program is not very versatile; suppose you have 61 unique bank account records -- then you would be SOL since you have only allocated an array of 60.

P.S.  You should consider heeding SomePeguin's advice:
> 
You should also have a look at the Collections Framework. I think a Map might be of use to you.

A Map would allow you to associate the account id as the key, whereas the value could be a class that contains the account attributes (id, balance, owner's name, etc).  You can quickly search the Map to verify whether the account id has already been added.

---

### Post by s3a on 2010-02-09
My teacher specifically told us to make 60. And what do you guys mean by "map"? As for the if statement, I originally had it as "if(!isDuplicate)" but my friend changed it. As for the for statement, I changed it to "for(int count = 0; count < index;)" and, I still don't get anything to be written in my output file.

All it ever says is "Sum of balances: 0.0" (in the output file).

Here is my new CustomerReport class:
```
import java.util.Scanner;
import java.io.*;

public class CustomerReport
{
   public static void main(String[] args) throws IOException
   {
      // Initialize sumBalance variable
	  double sumBalance = 0.0;
	  // Prompt user for and read file name
      System.out.print("Enter input file name: ");
      Scanner kb = new Scanner(System.in);
      String[] filename = new String[3];
      
      filename[0] = kb.next();

      
      BankAccount accounts[] = new BankAccount[60];

      // Create a scanner object and associate it with the input file
      Scanner fileReader = new Scanner(new File(filename[0]));

      // Prompt the user for and read the name of the error file.
      System.out.print("\nEnter the name of the error file to be written: ");
      filename[1] = kb.next();
      // Open the error file for writing.
      PrintWriter errorWrite = new PrintWriter(new File(filename[1]));
      
      // Prompt the user for and read the name of the report file.
      System.out.print("Enter the name of the report file for writing: ");
      filename[2] = kb.next();
      // Open the report file for writing.
      PrintWriter reportWrite = new PrintWriter(new File(filename[2]));
      
      // Read id, balance, and name items from each line and store them in a bank account if it is valid (Check program and comment!!!)
      int index = 0;
      while(fileReader.hasNextLine() && index < accounts.length)
      {
         int id = fileReader.nextInt();
         double balance = fileReader.nextDouble();
         String name = fileReader.nextLine();         
         
         if(id >= 11000 && id <= 11100 && balance >= 50.0)
         {
        	boolean isDuplicate = false;
        	System.out.printf("%5d  %10.2f  %20s\n", id, balance, name); // This line assumes no duplicates, therefore it is temporary.
            for(int count = 0; count < index;)
            {
	            if(id == accounts[count].getAccountNumber())            
	            {
	            	isDuplicate = true;
	            	errorWrite.printf("Invalid input on line #: %5d  %10.2f  %20s\n", accounts[count].getAccountNumber(), accounts[count].getBalance(), accounts[count].getName());
	            	if(accounts[index].getAccountNumber() == accounts[count].getAccountNumber())
	            		errorWrite.println("Duplicated account number");
	            }
	            else // Check if this is necessary (Right now I think that it is)
	            	isDuplicate = false;
            
            	// Check to see if it is a duplicate. If not, create the account, add its balance to the total balance, write it to the output file then increment index.
	            if(!isDuplicate)
	            {
	            	accounts[index] = new BankAccount(name, id, balance);
	            	sumBalance += accounts[index].getBalance();
	            	reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);	            	
	            	index++;
	            }
            }
         }
         else
         {           
        	 errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
        	 if(balance < 50)
         		errorWrite.println("Account balance must be at least 50.0 ");
         	 if(id < 11000 || id > 11100)
         		 errorWrite.println("Account Number must be between 11000 and 11100. ");
         }
      }
      // Write the sum of the balances to the file
      reportWrite.println("Sum of balances: " + sumBalance);
                  
      // Close the files:
      fileReader.close();
      errorWrite.close();
      reportWrite.close();
      
   }
}
```

---

### Post by Some Penguin on 2010-02-09
> **s3a said:**
> My teacher specifically told us to make 60. And what do you guys mean by "map"?

Perhaps a search for 'Java', 'Map', and 'Collections' would be enlightening.

> As for the if statement, I originally had it as "if(!isDuplicate)" but my friend changed it. As for the for statement, I changed it to "for(int count = 0; count < index;)" and, I still don't get anything to be written in my output file.

And if you're going to continue asking questions here, I suggest you actually pay attention to the answers, because otherwise there's no point in anybody spending any more time trying to help you.

Your for() loop that supposedly checks for duplicates still has the same problems that people have already pointed out to you.  You don't increment the loop variable -- ever.   You do the "if (!isDuplicate)" test *every time* you go through the loop, even though you logically can't know if it's a duplicate until you're finished.  If it DOES find a duplicate, you keep going -- and set the isDuplicate back to false if there are any more items, because they WON'T match. 

And no account ever gets created, because your account creation code only gets invoked in the for() loop, which only runs if count < index, which will never be true if there are no accounts yet because index is 0!

This is not exactly arcane.  If you actually reason through it and look systematically at what your code actually will do, it should be very clear that it's not going to work at all.

---

### Post by dwhitney67 on 2010-02-09
Here's my take on your CustomerReport.  Although I would have preferred to take command line args for the file names, I used your approach to query the user for the various file names.  See if the logic makes sense.
```

import java.util.Scanner;
import java.io.*;

public class CustomerReport
{
   public static void main(String[] args) throws IOException
   {
      Scanner kb = new Scanner(System.in);

      // Prompt the user for the data file
      System.out.print("Enter data file name: ");
      String dataFile = kb.next();

      // Prompt the user for the error file.
      System.out.print("\nEnter the name of the output error file: ");
      String errorFile = kb.next();

      // Prompt the user for the report file.
      System.out.print("Enter the name of the report file: ");
      String reportFile = kb.next();

      // Create a scanner object and associate it with the input file
      Scanner dataReader = new Scanner(new File(dataFile));

      // Open the error file and report files.
      PrintWriter errorWriter  = new PrintWriter(new File(errorFile));
      PrintWriter reportWriter = new PrintWriter(new File(reportFile));

      // Read id, balance, and name items from each line.  If the data is valid
      // create a bank account object to hold the data.
      double      sumBalance = 0.0;
      int         numAcct = 0;
      BankAccount[] accounts = new BankAccount[60];   // bad, bad, bad!!!

      while (dataReader.hasNextLine() && numAcct < accounts.length)
      {
         int    acctId  = dataReader.nextInt();
         double balance = dataReader.nextDouble();
         String name    = dataReader.nextLine();

         if (acctId >= 11000 && acctId <= 11100 && balance >= 50.0)
         {
            // for debug
            System.out.printf("%5d  %10.2f  %20s\n", acctId, balance, name);

            BankAccount acct = new BankAccount(name, acctId, balance);

            if (numAcct == 0)
            {
               // first account; implies that it is unique
               accounts[numAcct++] = acct;
               sumBalance += balance;
            }
            else
            {
               // verify account is unique
               boolean isUnique = true;

               for (int i = 0; i < numAcct && isUnique; ++i)
               {
                  // does this meet the reqs?  This allows for two or more individuals
                  // to have same account id, but yet different balance and/or name.
                  isUnique = !accounts[i].equals(acct);
               }

               if (isUnique)
               {
                  accounts[numAcct++] = acct;
                  sumBalance += balance;
               }
               else
               {
                  // acct is not unique!
                  errorWriter.println("Account is not unique: " + acct.toString());
               }
            }
         }
         else
         {
            errorWriter.printf("%5d  %10.2f  %20s", acctId, balance, name);

            if (balance < 50)
            {
               errorWriter.print("\tBalance < 50.0");
            }

            if (acctId < 11000 || acctId > 11100)
            {
               errorWriter.print("\tAccount Number not in [11000, 11100].");
            }
            errorWriter.println("");
         }
      }

      // Write the sum of the balances to the file
      for (int i = 0; i < accounts.length; ++i)
      {
         if (accounts[i] == null) break;

         reportWriter.println(accounts[i].toString() + "\n");
      }
      reportWriter.println("Sum of balances: " + sumBalance);

      // Close the files:
      dataReader.close();
      errorWriter.close();
      reportWriter.close();
   }
}

```
I changed some of your variable names, and reorganized the position of the declarations of others.

As for a map, a HashMap comes to mind.  Read more [here]("http://java.sun.com/javase/6/docs/api/java/util/HashMap.html").

---

