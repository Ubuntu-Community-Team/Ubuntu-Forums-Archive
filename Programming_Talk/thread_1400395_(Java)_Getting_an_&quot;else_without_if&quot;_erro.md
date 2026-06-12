---
title: "(Java) Getting an &quot;else without if&quot; error"
date: 2010-02-06
forum: Programming Talk
---

### Post by s3a on 2010-02-06
I am getting syntax errors with my CustomerReport class and I was hoping someone could help me figure out what I am doing wrong.

Here is the text file:
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

Here is the BankAccount class:
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

And here is the CustomerReport class (which is what I having trouble with:
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
         double balance = fileReader.nextDouble();
         String name = fileReader.nextLine();
         
         if(id >= 11000 && id <= 11100 && balance >= 50.0)
         {
            System.out.printf("%5d  %10.2f  %20s\n", id, balance, name);
            accounts[index] = new BankAccount(name, id, balance);
            [B]
            for(int count = 0; count < accounts.length; count++)//PART FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!!
            {
	            if(accounts[index].equals(accounts[count]));
	            	errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
	            else
	            	reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
            }//PART FOR MAKING SURE TWO ACCOUNTS ARE NOT THE SAME!!!!!![/B]
            
            //reportWrite.println(accounts[index].getName() + " " + accounts[index].getAccountNumber() + " " + accounts[index].getBalance());
            //reportWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
            sumBalance += accounts[index].getBalance();
            index++;
         }
         else
         {
            //reportWrite.println(accounts[index].getName() + " " + accounts[index].getAccountNumber() + " " + accounts[index].getBalance());
        	 errorWrite.printf("%5d  %10.2f  %20s\n", id, balance, name);
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
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   
   







   /*public static void main(String[] args) throws IOException
   {
      Scanner kb = new Scanner(System.in);
      System.out.print("Enter your name: ");
      String ownerName = kb.nextLine();
      System.out.println();
      System.out.print("Enter the name of the file you want to open: ");
      String filename = kb.nextLine();
      System.out.println();
      FileReader fileReader = new FileReader(filename);
      BufferedReader bufferedReader = new BufferedReader(fileReader);
      String lineReader = null;

      // Used to hold all bank account details of an individual in a string
      String[] bankAccounts = new String[60]; // Should probably make this an object of type BankAccount in revision of this program
      boolean[] valid = new boolean[60];
      // Used to extract ID from text file
      char[] charVariable = new char[5];
      // Used to convert 5 chars into 1 String
      String[] stringID = new String[60];
      //
      String[] stringBalance = new String[60];
      // Used to convert Strings to ints
      int[] intID = new int[60];

      for(int index = 0; index < 60; index++)
      {
         stringID[index] = "";
      }

      // Read each line in input file and extract the data
      for(int index = 0; index < bankAccounts.length; index++)
      {
         bankAccounts[index] = bufferedReader.readLine();

         // Get account IDs from file and then store them in intID
         for(int counter = 0; counter < 5; counter++)
         {
             stringID[index] += bankAccounts[index].charAt(counter);
             intID[index] = Integer.parseInt(stringID[index]);
         }
         System.out.println(intID[index]); // Print the account IDs for testing purposes

         // Get account balances - INCOMPLETE - counter is not accurate here
         for(int counter = 9; counter <= 14; counter++)
         {
            stringBalance[index] += bankAccounts[index].charAt(counter);
         }
         System.out.println(stringBalance[index]);
      }
      bufferedReader.close();
   }*/
}
```

The compilation error:
```
javac CustomerReport.java
CustomerReport.java:53: 'else' without 'if'
	            else
	            ^
CustomerReport.java:157: class, interface, or enum expected
}
^
2 errors

```

The error suggests that I have else without if but I don't see how that could be the problem. I made the part that I added later on in bold because, if I recall correctly, that's what caused the syntax errors.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by myrtle1908 on 2010-02-06
Have look at this line from CustomerReport ...

```
if(accounts[index].equals(accounts[count]));
```

Can you spot the problem?

---

### Post by HotCupOfJava on 2010-02-06
You have a semicolon at the end of your "if" statement - the compiler treats it as one line. Because you also have statements between it and the following else, the else appears to be hanging out there by itself as far as the compiler knows.

You also leave an unaccounted-for closing bracket at the end of the code that causes the second error

---

### Post by s3a on 2010-02-06
Thanks "Iron man" and myrtle! :)

---

