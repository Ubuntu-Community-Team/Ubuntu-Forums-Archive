---
title: "How do I go around using this private mutator/setter method? (Java)"
date: 2010-03-11
forum: Programming Talk
---

### Post by s3a on 2010-03-11
How can I avoid using the private setBalance() method. It can't be used in the first place. My teacher told us to make it private. I don't understand why you need a private method when you can access the variable only from within that specific class if you can access the variable directly.

But more importantly, how can I fix what I bolded?

Here is my BankApplication class (driver code):
```
import java.io.FileNotFoundException;
import java.util.Scanner;

public class BankApplication
{
	public static void main (String[] args)
	{
		Scanner kb = new Scanner(System.in);
		System.out.print("Enter bank name: ");
		String name = kb.nextLine();
		System.out.print("Enter initial capcity of bank accounts: ");
		int capacity = kb.nextInt();
		Bank bank = new Bank(name, capacity);
		bank.run();
	}
}
```

Here is my BankAccount class (definition of an account):
```
// Check if this class is necessary for Assignment_2A!

public class BankAccount
{
   private String name;
   private int accountNumber;
   private static double balance; // This apparently should not be static
   public static final double MIN_BALANCE = 50;
   public static final int MIN_ID = 11000;
   public static final int MAX_ID = 11100;

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
   public String toString()
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
   public static boolean isValidId()
   {
	   if(balance >= MIN_ID && balance <= MAX_ID)
	   	   return true; // Valid
	   else
		   return false; // Invalid
   }
   public static boolean isValidBalance()
   {
	   if(balance <= MIN_BALANCE)
		   return true; // Account has at least $50.0
	   else
		   return false; // Account has less than $50.0
   }
}
```

Here is my Bank class (the class I'm working on right now):
```
// package bankapplication; // He said to take it out

import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;
import java.util.Scanner;

public class Bank
{

    private String name;                 // bank name
    private BankAccount[] accountList;  // Bank's filing cabinet
    private int numAccounts;             //no. of accounts in the filing cabinet
    

    public Bank(String name, int maxAccounts) {
        this.name = name;
        accountList = new BankAccount[maxAccounts];
        numAccounts = 0;
        System.out.println("Welcome to " + name + " banking system");
    }

    public boolean isFull() {
        System.out.println("isFull - Fix it");
        return true;    // Fix it
    }

    public boolean isEmpty() {
        System.out.println("isEmpty - Fix it");
        return true;        // Fix it
    }

    //Creates a Bank Account with an initial balance and adds it to the account list
    
    public boolean openAccount(String name, int accountNumber, double initialBalance)
    {
    	accountList[numAccounts] = new BankAccount(name, accountNumber, initialBalance);
    	++numAccounts;
    	return true;
    }
    
    public void openNewAccount(/*String name, int accountNumber, double initialBalance*/)
    {
        //System.out.println("openNewAccount - Fix it");
        //accountList[numAccounts - 1] = new BankAccount(name, accountNumber, initialBalance);
    }

    public boolean exists(int accNum)
    {
    	return  ( findAccount(accNum) != null );
    }
    // close an account with a given number
    public boolean closeAccount(int accNum)
    {
    	boolean result = false;
    	int position = this.findAccountPosition(accNum);
    	if( position == -1)
    	{
    		System.out.println("Account not found. Your account cannot be closed.");
    		return false;
    	}
    	
    	System.out.println("Your account is about to be closed.");
    	--numAccounts;
    	for(int count = position; count < numAccounts; count++)
    	{
    		accountList[count] = accountList[count+1];
    	}
    	System.out.println("Your account is now closed.");
    	return true;
    	
//        for(int count = 0; count < numAccounts; count++)
//        {
//        	if(accNum == accountList[count].getAccountNumber())
//        	{
//        		
//        		accountList[count] = null;
//        		System.out.println("Your account has been closed.");
//        		result =  true;
//        	}
//        	else
//        	{
//        		System.out.println("Your account cannot be closed.");
//        		result =  false;
//        	}
//        }

    }

    // Gets the sum of the balances of all accounts in this bank.
    public double getTotalBalance()
    {
    	double totalBalance = 0;
    	for(int count = 0; count < accountList.length; ++count)
    	{
    		 if(exists(accountList[count].getAccountNumber()))
    	     {
    			 totalBalance += accountList[count].getBalance();
    	     }
    	}
    	return totalBalance;
    }

    // Counts the number of bank accounts whose balance is at
    // least a given value.
    public int countAccountsWithBalaceOver(double minAmount) {
        System.out.println("countAccountsWithBalaceOver - Fix it");
        // Fix it
        return -1;

    }

    //Finds a bank account with a given number.
    // Return the account with the given number, or null if there
    // is no such account.
    public BankAccount findAccount(int accountNumber) {
        System.out.println("findAccount - Fix it");
        // Fix it
        return null; // No match in the entire array list
    }

    public int findAccountPosition(int accountNumber)
    {
    	
    	int position = 0;
    	while(accountList[position].getAccountNumber() != accountNumber)
    	{
    		if(accountList[position].getAccountNumber() == accountNumber)
    		{
    			
    		}
    		position++; // Think about using count instead of position because of 0 being position 1, unless position 0 is a position
    	}
    	return position;
//        System.out.println("findAccountPosition - Fix it");
//        int position = -1;
//        // Fix it
//        return position;
    }

    // Gets the bank account with the largest balance.
    // Return the account with the largest balance, or null if the
    // bank has no accounts
    public BankAccount getHighestBalance() {
 
        System.out.println("getHighestBalance - Fix it");
        if()
        	return accountList[numAccounts - 1];
        else
        	return null;    // Fix it
    }

 // Deposit method handles transactions that deposit money into bank account
    public boolean deposit(int accNum, double amount){
    	boolean result = false;
    	if(amount < 0.0)
    	{
    		System.out.println("Can not deposit a negative amount");
    		result = false;
    	}
        System.out.println("Deposited $" + amount + " into account.");
        if(amount >= 0.01)
        {
        	**accountList[numAccounts].setBalance(accountList[numAccounts].getBalance() + amount); // Set balance is a private method, what do I do to get around this?**
        	result = true;
        }
        else
        {
        	result = false;
        }
        return result;
        }

    // Withdraw method handles transactions that withdraw money from the bank account
    public boolean withdraw(int accNum, double amount)
    {
    	for(int count = 0; count < accountList.length; count++)
    	**accountList[count].setBalance(accountList[count].getBalance() - amount); // Set balance is a private method, what do I do to get around this?**
    }

    public double getBalance(int accNum) {
        BankAccount anAccount = this.findAccount(accNum);
        if (anAccount == null) {
            System.out.println("Error in Bank getBalance: account number " + accNum + " does not exist");
        }

        return anAccount.getBalance();
    }

    public String getName() {
        return name;
    }

    public int getNumberOfAccounts() {
        return numAccounts;
    }

    public void printSummary() {
        System.out.println(getName() + ": " + getNumberOfAccounts() + " of "
                + accountList.length + " accounts open");
    }

    @Override
    public String toString() {
        String result = "\n    ID   balance  Name"
                + "\n    ==================";
        for (int k = 0; k < numAccounts; ++k) {
            result += "\n  " + accountList[k];
        }
        result += "\n    ==================";
        result += "\n" + getName() + ": " + getNumberOfAccounts()
                + " of " + accountList.length + " accounts open\n";
        return result;
    }

    private char yesno(String prompt) {
        char answer;
        do {
            System.out.print(prompt);
            Scanner kb = new Scanner(System.in);
            answer = kb.nextLine().charAt(0);
            answer = Character.toLowerCase(answer);
        } while (answer != 'n' && answer != 'y');
        return answer;
    }

    private static int readInt(String prompt) {
        Scanner scan = new Scanner(System.in);
        int intValue = 0;
        boolean finished = false;
        do {
            System.out.print(prompt);
            if (scan.hasNextInt()) {
                intValue = scan.nextInt();
                finished = true;

            } else {
                String junk = scan.nextLine();
                System.out.println("Bad input: " + junk + " Must be an integer value.");
            }
        } while (!finished);
        return intValue;
    }

    private static int readAccountNumber() {

        Scanner scan = new Scanner(System.in);
        int accNum;
        do {
            accNum = readInt("Enter account number in the range ["
                    + BankAccount.MIN_ID + ", " + BankAccount.MAX_ID + "]: ");
        } while (!BankAccount.isValidAccountNumber(accNum));
        return accNum;
    }

    private static double readDouble(String prompt) {
        Scanner scan = new Scanner(System.in);
        double dblValue = 0;
        boolean finished = false;
        do {
            System.out.print(prompt);
            if (scan.hasNextDouble()) {
                dblValue = scan.nextDouble();
                finished = true;
            } else {
                String junk = scan.nextLine();
                System.out.println("Bad input: " + junk
                        + " Must be a double value.");
            }
        } while (!finished);
        return dblValue;
    }

    private static double readBalance() {
        Scanner scan = new Scanner(System.in);
        double bal;
        do {
            bal = readDouble("Enter an initial balance ( >= "
                    + BankAccount.MIN_BALANCE + " ) : ");
        } while (!BankAccount.isValidBalance(bal));
        return bal;
    }

    private static String getString(String prompt) {
        Scanner scan = new Scanner(System.in);
        System.out.print(prompt);
        return scan.nextLine();
    }

    private static void printMenu() {
        System.out.print("\nOptions: \n"
                + "     o) Open a new account\n"
                + "     c) Close an existing account\n"
                + "     d) Deposit into an account\n"
                + "     w) Withdraw from an account\n"
                + "     p) Print all accounts\n"
                + "     s) Show a bank record\n"
                + "     t) Total all account balance amounts\n"
                + "     k) Count accounts with balances over a specified amount\n"
                + "     q) Quit\n"
                + "Enter your choice: ");

    }

    private static char getChoice() {
        Scanner scan = new Scanner(System.in);
        char choice;
        boolean done = false;
        do {
            printMenu();
            choice = scan.nextLine().charAt(0);     // allow case insensitive
            choice = Character.toLowerCase(choice); // convert to lower case
            switch (choice) {
                case 'o':
                case 'c':
                case 'd':
                case 'w':
                case 'p':
                case 'q':
                case 's':
                case 't':
                case 'k':
                    done = true;
                    break;
                default:
                    System.out.println("bad choice. try again!");
            }
        } while (!done);
        return choice;
    }

    private void loadDatabase() throws FileNotFoundException {
        Scanner scan = new Scanner(System.in);
        int id;
        double amt;
        String ownername, filename;

        // open the filing cabinet
        filename = getString("\nEnter bank database file name: ");
        System.out.println("Thank you.");
        System.out.println("About to start loading bank records");
        Scanner fileScanner = new Scanner(new File(filename));
        while (fileScanner.hasNextLine() && !isFull()) {
            id = fileScanner.nextInt();
            amt = fileScanner.nextDouble();
            ownername = fileScanner.nextLine();
            openNewAccount(ownername, id, amt);
        }
        System.out.println("Finished loading bank records");
        fileScanner.close();

    }

    public void quit() throws FileNotFoundException {
        Scanner scan = new Scanner(System.in);
        String filename;

        // open the filing cabinet
        char answer = yesno("Warning: do you wish to update the bank database file (y/n)? ");
        if (answer == 'n') {
            return;   // nothing to do
        }
        System.out.println();
        filename = getString("\nEnter update file name: ");
        System.out.println("Thank you.");
        System.out.println("About to save database to file: " + filename);
        PrintWriter pw = new PrintWriter(new File(filename));

        for (int k = 0; k < numAccounts; ++k) {
            pw.println(accountList[k]);
        }

        System.out.println("Finished saving bank records");
        pw.close();
        System.out.println("The " + name
                + " banking system is now shutting down . . .");


    }

    private void openNewBankAccount() {
        if (isFull()) {
            System.out.println("Bank full - no room for more bank accounts");
            return;
        }
        int id = readAccountNumber();
        double amt = readBalance();
        String ownername = getString("Enter owner's name: ");
        openNewAccount(ownername, id, amt);

    }

    private void removeBankAccount() {
        // Fix it
        System.out.println("removeBankAccount - Fix it");
    }

    private boolean depositIntoAnAccount(){
        int id = readAccountNumber();
        double amt = readDouble("Enter deposit amount ( >= 0 ): ");
        return deposit(id, amt);
    }

    private boolean withdrawFromAnAccount() {
        int id = readAccountNumber();
        double amt = readDouble("Enter withdraw amount ( >=0 ): ");
        return withdraw(id, amt);

    }

    private void showBankRecord() {
        System.out.println("showBankRecord - Fix it");
        // Fix it
    }

    private void totalAllAccountBalanceAmounts() {
        System.out.println("totalAllAccountBalanceAmounts - Fix it");
        // Fix it
    }

    public void countAccountsWithBalancesOverSpecifiedAmount() {
        System.out.println("countAccountsWithBalancesOverSpecifiedAmount - Fix it");
        // Fix it
        // I think he added the following in class:
        /*double amt = this.readDouble("Enter an amount"); //
        int count = 0;
        for(int k = 0; k < numAccounts; ++k)
        {
        	if(accountList[k].getBalance() >= amt) ++count;
        }*/
    }

    public void run() throws FileNotFoundException
    {
        loadDatabase();    // Load account list from file
        char choice;
        do {
            choice = getChoice();
            switch (choice) {
                case 'o':
                    openNewBankAccount();
                    break;
                case 'c':
                    removeBankAccount();
                    break;
                case 'd':
                    depositIntoAnAccount();
                    break;
                case 'w':
                    withdrawFromAnAccount();
                    break;
                case 'p':
                    System.out.println(this);
                    break;
                case 's':
                    showBankRecord();
                    break;
                case 't':
                    totalAllAccountBalanceAmounts();
                    break;
                case 'k':
                    countAccountsWithBalancesOverSpecifiedAmount();
                    break;
                case 'q':
                    quit();
            }
        } while (choice != 'q');
    }
}
```

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2010-03-11
The constructor should initialize the balance.  That's a given.

Now, the customer has two choices:  deposit(amount) or withdraw(amount).

If it is a savings account:  addPeriodicInterest().

In each of these cases, the setBalance() method is not required to be public.

Hopefully, with your electric bill paid in full, the light bulb above your head will illuminate.

---

