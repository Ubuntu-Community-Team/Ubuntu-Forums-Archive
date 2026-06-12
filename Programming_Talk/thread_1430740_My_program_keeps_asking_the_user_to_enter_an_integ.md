---
title: "My program keeps asking the user to enter an integer and doesn't move on! (Java)"
date: 2010-03-15
forum: Programming Talk
---

### Post by s3a on 2010-03-15
_The following is a sample run of what should happen (I bolded where I am stuck - it doesn't let me go further than that):_
```
Here is a sample run:
Enter bank name: Vanier
Enter initial capacity of bank accounts: 5
Welcome to Vanier banking system
Enter bank database file name: empty.txt
Thank you.
About to start loading bank records
Finished loading bank records
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Bank Empty - no bank accounts to close
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    ==================
Vanier: 0 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: o
**Enter account number in the range [111, 999]: 111**
Enter an initial balance ( >= 50.0 ) : 100.0
Enter owner’s name: One Une
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
      q) Quit
Enter  your choice: o
Enter  account number in the range [111, 999]: 222
Enter  an initial balance ( >= 50.0 ) : 200.0
Enter  owner’s name: Twenty Two
Options:
      o) Open a new account
      c) Close an existing account
      d) Deposit into an account
      w) Withdraw from an account
      p) Print all accounts
      s) Show a bank record
      t) Total all account balance amounts
      k) Count accounts with balances over a specified amount
      q) Quit
Enter your choice: o
Enter account number in the range [111, 999]: 444
Enter an initial balance ( >= 50.0 ) : 400
Enter owner’s name: Forty Four
Options:
      o) Open a new account
      c) Close an existing account
      d) Deposit into an account
      w) Withdraw from an account
      p) Print all accounts
      s) Show a bank record
      t) Total all account balance amounts
      k) Count accounts with balances over a specified amount
      q) Quit
Enter your choice: p
    ID    balance Name
    ==================
    111    100.00 One Une
    222    200.00 Twenty Two
    444    400.00 Forty Four
    ==================
Vanier: 3 of 5 accounts open
Options:
      o) Open a new account
      c) Close an existing account
      d) Deposit into an account
      w) Withdraw from an account
      p) Print all accounts
      s) Show a bank record
      t) Total all account balance amounts
      k) Count accounts with balances over a specified amount
      q) Quit
Enter your choice: d
Enter account number in the range [111, 999]: 123
Enter deposit amount ( >= 0 ): 100.0
Error in Bank deposit: account number 123 does not exist
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: d
Enter account number in the range [111, 999]: 111
Enter deposit amount ( >= 0 ): 150.0
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    111   250.00 One Une
    222   200.00 Twenty Two
    444   400.00 Forty Four
    ==================
Vanier: 3 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: o
Enter account number in the range [111, 999]: 333
Enter an initial balance ( >= 50.0 ) : 300.0
Enter owner’s name: Thirty Three
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: o
Enter account number in the range [111, 999]: 555
Enter an initial balance ( >= 50.0 ) : 500.50
Enter owner’s name: Fifty Five
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    111   250.00 One Une
    222   200.00 Twenty Two
    444   400.00 Forty Four
    333   300.00 Thirty Three
    555   500.50 Fifty Five
    ==================
Vanier: 5 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: o
Bank full - no room for more bank accounts
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 321
Account number 321 does not exists. No account closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 444
Account to be removed:
  444    400.00 Forty Four
Are you sure you want to close (remove and discard) this account (y/n)? x
Are you sure you want to close (remove and discard) this account (y/n)? y
Account 444 is now permanently closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID    balance Name
    ==================
    111    250.00 One Une
    222    200.00 Twenty Two
    333    300.00 Thirty Three
    555    500.50 Fifty Five
    ==================
Vanier: 4 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: t
Total of all bank balance amounts: 1250.5
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: k
Enter an initial balance ( >= 50.0 ) : 260.0
There are 2 accounts with balances over $260.00
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: w
Enter account number in the range [111, 999]: 555
Enter withdraw amount ( >=0 ): 155.55
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    111   250.00 One Une
    222    200.00 Twenty Two
    333    300.00 Thirty Three
    555    344.95 Fifty Five
    ==================
Vanier: 4 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 222
Account to be removed:
  222    200.00 Twenty Two
Are you sure you want to close (remove and discard) this account (y/n)? y
Account 222 is now permanently closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID    balance Name
    ==================
    111    250.00 One Une
    333    300.00 Thirty Three
    555    344.95 Fifty Five
    ==================
Vanier: 3 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 111
Account to be removed:
  111    250.00 One Une
Are you sure you want to close (remove and discard) this account (y/n)? y
Account 111 is now permanently closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID    balance Name
    ==================
    333    300.00 Thirty Three
    555    344.95 Fifty Five
    ==================
Vanier: 2 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 555
Account to be removed:
  555    344.95 Fifty Five
Are you sure you want to close (remove and discard) this account (y/n)? y
Account 555 is now permanently closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    333   300.00 Thirty Three
    ==================
Vanier: 1 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 111
Account number 111 does not exists. No account closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    333   300.00 Thirty Three
    ==================
Vanier: 1 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: d
Enter account number in the range [111, 999]: 333
Enter deposit amount ( >= 0 ): 30.33
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID    balance Name
    ==================
    333    330.33 Thirty Three
    ==================
Vanier: 1 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: c
Enter account number in the range [111, 999]: 333
Account to be removed:
  333    330.33 Thirty Three
Are you sure you want to close (remove and discard) this account (y/n)? y
Account 333 is now permanently closed
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    ==================
Vanier: 0 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: o
Enter account number in the range [111, 999]: 777
Enter an initial balance ( >= 50.0 ) : 700.00
Enter owner’s name: Seventy Seven
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: p
    ID   balance Name
    ==================
    777   700.00 Seventy Seven
    ==================
Vanier: 1 of 5 accounts open
Options:
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: q
Warning: do you wish to update the bank database file (y/n)? Warning: do you wish to update the bank da
y
Enter update file name: newdatabase.txt
Thank you.
About to save database to file: newdatabase.txt
Finished saving bank records
The Vanier banking system is now shutting down . . .
BUILD SUCCESSFUL (total time: 12 minutes 42 seconds)
The Vanier banking system is now shutting down . . .
```



_Here is my Bank class (what I am currently working on and should be where the error is):_
```
// package bankapplication; // He said to take it out

import java.io.File;
import java.io.FileNotFoundException;
import java.io.PrintWriter;
import java.util.Scanner;

public class Bank
{

    private String bankName; // Used to be called name - put a comment just in case
    private BankAccount[] accountList;  // Bank's filing cabinet
    private int numAccounts;             //No. of accounts in the filing cabinet

    public Bank(String bankName, int maxAccounts)
    {
        this.bankName = bankName;
        accountList = new BankAccount[maxAccounts];
        numAccounts = 0;
        System.out.println("Welcome to " + bankName + " banking system");
    }

    public boolean isFull()
    {
        if(accountList.length == numAccounts)
        {
        	return true;	
        }
        else
        {
        	return false;
        }
    }

    public boolean isEmpty()
    {
	    if(numAccounts == 0)
	    {
	    	return true;
	    }
	    else
	    {
	    	return false;
	    }
    }

    //Creates a Bank Account with an initial balance and adds it to the account list
    
    public boolean openAccount(String name, int accountNumber, double initialBalance)
    {
    	// This method still needs some fixing
    	boolean result = false;
    	if(numAccounts != 0)
    	{
    		accountList[numAccounts - 1] = new BankAccount(name, accountNumber, initialBalance);
    		result = true;
    	}
    	++numAccounts;
    	return result;
    }

    public boolean exists(int accNum)
    {
    	return  ( findAccount(accNum) != null );
    }

    // Close an account with a given number
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
    public int countAccountsWithBalanceOver(double minAmount)
    {
    	int counter = 0;
    	
    	for(int count = 0; count < numAccounts; ++count)
    	{
    		if(accountList[count].getBalance() > minAmount)
    		{
    			counter++;
    		}
    	}
    	return counter;
    }

    //Finds a bank account with a given number.
    // Return the account with the given number, or null if there
    // is no such account.
    public BankAccount findAccount(int accountNumber)
    {
    	return accountList[findAccountPosition(accountNumber)];
    }

    public int findAccountPosition(int accountNumber)
    {
    	// The following is in the case that an account will be found
    	int position = 0;
    	while(accountList[position].getAccountNumber() != accountNumber)
    	{
    		if(accountList[position].getAccountNumber() == accountNumber)
    		{
    			break;
    		}
    		else
    		{
    			position++;
    		}    		
    	}
    	return position;
    	// I think something needs to be implemented for the case that no account with such an accountNumber is found, ie returning -1
    	}

    // Gets the bank account with the largest balance.
    // Return the account with the largest balance, or null if the
    // bank has no accounts
    public BankAccount getHighestBalance()
    {
    	int largest = 0;
    	for(int count = 0; count < numAccounts; ++count)
    	{
    		
    		while(accountList[count + 1].getBalance() > accountList[count].getBalance())
        	{
        		largest = count + 1;
        	}
    	}
    	return accountList[largest];
    }

 // Deposit method handles transactions that deposit money into bank account
    public boolean deposit(int accNum, double amount)
    {
    	boolean result = false;
    	if(exists(accNum))
    	{
    		accountList[findAccountPosition(accNum)].deposit(amount);
    		result = true;
    	}
    	return result;
    }

    // Withdraw method handles transactions that withdraw money from the bank account
    public boolean withdraw(int accNum, double amount)
    {
    	boolean result = false;
    	if(exists(accNum))
    	{
    		accountList[findAccountPosition(accNum)].widthdraw(amount);
    		result = true;
    	}
    	return result;
    }

    public double getBalance(int accNum) {
        BankAccount anAccount = this.findAccount(accNum);
        if (anAccount == null)
        {
            System.out.println("Error in Bank getBalance: account number " + accNum + " does not exist");
        }

        return anAccount.getBalance();
    }

    public String getBankName() // used to be getName() - switched it but kept comment just in case
    {
        return bankName;
    }

    public int getNumberOfAccounts()
    {
        return numAccounts;
    }

    public void printSummary()
    {
        System.out.println(getBankName() + ": " + getNumberOfAccounts() + " of "
                + accountList.length + " accounts open");
    }

    @Override
    public String toString()
    {
        String result = "\n    ID   balance  Name"
                + "\n    ==================";
        for (int k = 0; k < numAccounts; ++k) {
            result += "\n  " + accountList[k];
        }
        result += "\n    ==================";
        result += "\n" + getBankName() + ": " + getNumberOfAccounts()
                + " of " + accountList.length + " accounts open\n";
        return result;
    }

    private char yesno(String prompt)
    {
        char answer;
        do {
            System.out.print(prompt);
            Scanner kb = new Scanner(System.in);
            answer = kb.nextLine().charAt(0);
            answer = Character.toLowerCase(answer);
        } while (answer != 'n' && answer != 'y');
        return answer;
    }

    private static int readInt(String prompt)
    {
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

    private static int readAccountNumber()
    {
        Scanner scan = new Scanner(System.in);
        int accNum;
        do {
            accNum = readInt("Enter account number in the range ["
                    + BankAccount.MIN_ID + ", " + BankAccount.MAX_ID + "]: ");
        }while (!BankAccount.isValidAccountNumber(accNum));
        return accNum;
    }

    private static double readDouble(String prompt)
    {
        Scanner scan = new Scanner(System.in);
        double dblValue = 0;
        boolean finished = false;
        do {
            System.out.print(prompt);
            if (scan.hasNextDouble()) {
                dblValue = scan.nextDouble();
                finished = true;
            }
            else
            {
                String junk = scan.nextLine();
                System.out.println("Bad input: " + junk
                        + " Must be a double value.");
            }
        } while (!finished);
        return dblValue;
    }

    private static double readBalance()
    {
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
                    System.out.println("Bad choice. Try again!");
            }
        } while (!done);
        return choice;
    }
    private void loadDatabase() throws FileNotFoundException
    {
        Scanner scan = new Scanner(System.in);
        int id;
        double amt;
        String ownername, filename;

        // Open the filing cabinet
        filename = getString("\nEnter bank database file name: ");
        System.out.println("Thank you.");
        System.out.println("About to start loading bank records");
        Scanner fileScanner = new Scanner(new File(filename));
        while (fileScanner.hasNextLine() && !isFull())
        {
            id = fileScanner.nextInt();
            amt = fileScanner.nextDouble();
            ownername = fileScanner.nextLine();
            openAccount(ownername, id, amt);
        }
        System.out.println("Finished loading bank records");
        fileScanner.close();
    }
    public void quit() throws FileNotFoundException
    {
        Scanner scan = new Scanner(System.in);
        String filename;

        // Open the filing cabinet
        char answer = yesno("Warning: do you wish to update the bank database file (y/n)? ");
        if (answer == 'n') {
            return;   // Nothing to do
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
        System.out.println("The " + bankName
                + " banking system is now shutting down . . .");

    }
    
    private void openNewBankAccount()
    {
        if (isFull())
        {
            System.out.println("Bank full - no room for more bank accounts");
            return;
        }
        else
        {
        	int id = readAccountNumber();
        	double amount = readBalance();
            String ownername = getString("Enter owner's name: ");
            openAccount(ownername, id, amount);
            return;
        }
        
    }

    private boolean removeBankAccount()
    {
    	if(isEmpty())
    	{
    		System.out.println("Bank Empty - no bank accounts to close");
    		return false;
    	}
    	else
    	{
    		return(closeAccount(readInt("Enter account number in the range [111, 999]:"))); // Is this the proper range or was my other range wrong - this range is what he put in the sample run
    	}
    }

    private boolean depositIntoAnAccount()
    {
        int id = readAccountNumber();
        double amt = readDouble("Enter deposit amount ( >= 0 ): ");
        return deposit(id, amt);
    }

    private boolean withdrawFromAnAccount() {
        int id = readAccountNumber();
        double amt = readDouble("Enter withdraw amount ( >=0 ): ");
        return withdraw(id, amt);

    }

    private void showBankRecord()
    {
    	int accountNumber = readInt("Enter the account number to view its record.");
    	if(exists(accountNumber))
    	{
    		System.out.println(findAccount(accountNumber));	
    	}
    	else
    	{
    		System.out.print("Error"); // Make this more meaningful
    	}
    }

    private void totalAllAccountBalanceAmounts()
    {
    	System.out.println("Total balance: " + getTotalBalance());
    }

    public void countAccountsWithBalancesOverSpecifiedAmount()
    {
    	double amount = readDouble("sdh");
        System.out.println("There are " + count(amount) + " accounts with balances exceeding $" + amount);
    }
    
    public int count(double amount)
    {
    	int counter = 0;
    	for(int index = 0; index < numAccounts; index++)
    	{
    		if(accountList[index].getBalance() > amount)
    		{
    			counter++;
    		}
    	}
    	return counter;
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

_Here is my BankAccount class:_
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
	   {
		   return true; // Valid
	   }
	   else
	   {
		   return false; // Invalid
	   }
   }
   public static boolean isValidBalance(double balance)
   {
	   if(balance <= MIN_BALANCE)
	   {
		   return true; // Account has at least $50.0
	   }
	   else
	   {
		   return false; // Account has less than $50.0
	   }
   }
public static boolean isValidAccountNumber(int accNum)
{
	if(accNum >= MIN_ID && accNum <= MAX_ID)
	{
		return true; // Valid
	}
	else
	{
		return false; // Invalid
	}
}
}
```

_Here is my BankApplication class (=Driver code):_
```
import java.io.FileNotFoundException;

import java.util.Scanner;



public class BankApplication

{

	public static void main (String[] args) throws FileNotFoundException

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

_Here is the sample run of when I run it (the previous one was what my teacher gave us) (I got straight to the point/error):_

```
Enter bank name: Vanier
Enter initial capcity of bank accounts: 5
Welcome to Vanier banking system

Enter bank database file name: empty.txt
Thank you.
About to start loading bank records
Finished loading bank records

Options: 
     o) Open a new account
     c) Close an existing account
     d) Deposit into an account
     w) Withdraw from an account
     p) Print all accounts
     s) Show a bank record
     t) Total all account balance amounts
     k) Count accounts with balances over a specified amount
     q) Quit
Enter your choice: o
Enter account number in the range [11000, 11100]: 111
Enter account number in the range [11000, 11100]: 
```

I tried tracing the error but each method "sends" me looking to another one and I can't find any errors. Given that I am somewhat new to this stuff still, I think I am missing something obvious or tricky. If someone could point out my mistake, I would again very much appreciate it!

Thanks in advance!

---

### Post by andrewc6l on 2010-03-15
Looks like your code wants a number between:
[11000, 11100]

When you enter 111, that's not in the range so it asks for a different number.

---

### Post by s3a on 2010-03-16
Ok thanks, so I fixed that bug but now I noticed that the balance instead of having 50.0 or more being considered valid, it's 50.0 or less (which is not what I want). I'm very exhausted so I'll go to bed and see if i can see what I did wrong tomorrow but if you see this before then and if it's not a big deal for you, could you please point me to what could potentially be the error?

---

### Post by Linteg on 2010-03-16
[php]
public static boolean isValidBalance(double balance)
{
   if(balance <= MIN_BALANCE)
   {
      return true; // Account has at least $50.0
   }
   ...
[/php]

---

### Post by Nevon on 2010-03-16
> **Linteg said:**
> [php]
public static boolean isValidBalance(double balance)
{
   if(balance <= MIN_BALANCE)
   {
      return true; // Account has at least $50.0
   }
   ...
[/php]

That can't be right. Shouldn't it be the other way around? If balance >= MIN_BALANCE the account has at least $50.0.

---

### Post by s3a on 2010-03-16
Yes, it should. Thanks! (I was only looking at the Bank class which I shouldn't of been doing)

---

### Post by s3a on 2010-03-16
Sorry for posting again but I modified the following:

```
public boolean openAccount(String name, int accountNumber, double initialBalance)
    {    	
    	boolean result;
    	if(exists(accountNumber) || numAccounts == accountList.length || BankAccount.isValidAccountNumber(accountNumber) == false || BankAccount.isValidBalance(initialBalance) == false)
    	{
    		result = false;
    	}
    	else
    	{
**    		accountList[numAccounts] = new BankAccount(name, accountNumber, initialBalance); // I thought the bug was here**
    		++numAccounts;
    		result = true;
    	}
    	return result;
    }
```

thinking that the current null pointer exception bug would be there but I realized that I ended fixing another bug which is unrelated to the issue I am having because the bolded line used to have accountList[numAccounts - 1] instead of accountList[numAccounts] but I now realize that, the way I have it now is the correct way. I'm also somewhat new to eclipse so when I run the debug tool I don't understand exactly what it is saying but I'll ask my teacher that when I'm off break.

---

