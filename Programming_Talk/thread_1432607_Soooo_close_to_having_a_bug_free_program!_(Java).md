---
title: "Soooo close to having a bug free program! (Java)"
date: 2010-03-18
forum: Programming Talk
---

### Post by s3a on 2010-03-18
I am so close to having a bug-free program! Creating an account usually works except for some reason after a long while of interaction with the program, at some point, it begins to just refuse to create a new account. I confirmed that it actually does not create a new account by trying to close the account (it says there is no account to close). I also told the program to print all accounts and it says there are none.

**_Here is my (most recent) user interaction:_**
```
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

    ID   balance  Name
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
Enter account number in the range [111, 999]: 111
Enter an initial balance ( >= 50.0 ) : 100.0
Enter owner's name: One Une

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
Enter account number in the range [111, 999]: 222
Enter an initial balance ( >= 50.0 ) : 200.0
Enter owner's name: Twenty Two

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
Enter owner's name: Forty Four

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

    ID   balance  Name
    ==================
  Name: One Une
Account Number: 111
Balance: 100.0
  Name: Twenty Two
Account Number: 222
Balance: 200.0
  Name: Forty Four
Account Number: 444
Balance: 400.0
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
Enter owner's name: Thirty Three

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
Enter owner's name: Fifty Five

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

    ID   balance  Name
    ==================
  Name: One Une
Account Number: 111
Balance: 100.0
  Name: Twenty Two
Account Number: 222
Balance: 200.0
  Name: Forty Four
Account Number: 444
Balance: 400.0
  Name: Thirty Three
Account Number: 333
Balance: 300.0
  Name: Fifty Five
Account Number: 555
Balance: 500.5
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
Enter account number in the range [111, 999]:321
Account number 321 does not exists. No account closed.

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
Enter account number in the range [111, 999]:444
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?x
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 444 is now permanently closed.

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

    ID   balance  Name
    ==================
  Name: One Une
Account Number: 111
Balance: 100.0
  Name: Twenty Two
Account Number: 222
Balance: 200.0
  Name: Thirty Three
Account Number: 333
Balance: 300.0
  Name: Fifty Five
Account Number: 555
Balance: 500.5
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
Total balance: 1100.5

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
Enter deposit amount ( >= 0 ): 150

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
Total balance: 1250.5

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

    ID   balance  Name
    ==================
  Name: One Une
Account Number: 111
Balance: 250.0
  Name: Twenty Two
Account Number: 222
Balance: 200.0
  Name: Thirty Three
Account Number: 333
Balance: 300.0
  Name: Fifty Five
Account Number: 555
Balance: 500.5
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
Enter your choice: k
Enter the minimum amount.260
There are 2 accounts with balances exceeding $260.0

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

    ID   balance  Name
    ==================
  Name: One Une
Account Number: 111
Balance: 250.0
  Name: Twenty Two
Account Number: 222
Balance: 200.0
  Name: Thirty Three
Account Number: 333
Balance: 300.0
  Name: Fifty Five
Account Number: 555
Balance: 344.95
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
Enter account number in the range [111, 999]:222
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 222 is now permanently closed.

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

    ID   balance  Name
    ==================
  Name: One Une
Account Number: 111
Balance: 250.0
  Name: Thirty Three
Account Number: 333
Balance: 300.0
  Name: Fifty Five
Account Number: 555
Balance: 344.95
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
Enter account number in the range [111, 999]:111
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 111 is now permanently closed.

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

    ID   balance  Name
    ==================
  Name: Thirty Three
Account Number: 333
Balance: 300.0
  Name: Fifty Five
Account Number: 555
Balance: 344.95
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
Enter account number in the range [111, 999]:555
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 555 is now permanently closed.

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

    ID   balance  Name
    ==================
  Name: Thirty Three
Account Number: 333
Balance: 300.0
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
Enter account number in the range [111, 999]:111
Account number 111 does not exists. No account closed.

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

    ID   balance  Name
    ==================
  Name: Thirty Three
Account Number: 333
Balance: 300.0
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

    ID   balance  Name
    ==================
  Name: Thirty Three
Account Number: 333
Balance: 330.33
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
Enter account number in the range [111, 999]:333
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 333 is now permanently closed.

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

    ID   balance  Name
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
Enter an initial balance ( >= 50.0 ) : 700.0
Enter owner's name: Seventy Seven

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

    ID   balance  Name
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
Enter an initial balance ( >= 50.0 ) : 700.0
Enter owner's name: Seventy Seven

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

    ID   balance  Name
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
Enter your choice: p

    ID   balance  Name
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
Enter an initial balance ( >= 50.0 ) : 700.0
Enter owner's name: Seventy Seven

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

    ID   balance  Name
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
Enter your choice: o
Enter account number in the range [111, 999]: 777
Enter an initial balance ( >= 50.0 ) : 777
Enter owner's name: 777

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

    ID   balance  Name
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
Enter your choice: 777
Bad choice. Try again!

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
Enter your choice: 

```

_**Here is my Bank class (most likely where the bug is located):**_
```
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
    	boolean result;
    	if(exists(accountNumber) || numAccounts == accountList.length || BankAccount.isValidAccountNumber(accountNumber) == false || BankAccount.isValidBalance(initialBalance) == false)
    	{
    		result = false;
    	}
    	else
    	{
    		accountList[numAccounts] = new BankAccount(name, accountNumber, initialBalance);
    		++numAccounts;
    		result = true;
    	}
    	return result;
    }

    public boolean exists(int accNum)
    {
    	return  ( findAccount(accNum) != null );
    }

    // Close an account with a given number
    public boolean closeAccount(int accountNumber)
    {
    	boolean result = false;
    	int position = this.findAccountPosition(accountNumber);
    	if( position == -1)
    	{
    		System.out.println("Account number " + accountNumber + " does not exists. No account closed.");
    	}
    	else
    	{
    		System.out.println("Your account is about to be closed.");
    		if(yesno("Are you sure you want to close (remove and discard) this account (y/n)?") == 'y')
	    	{
    			--numAccounts;
    	    	for(int count = position; count < numAccounts; count++)
    	    	{
    	    		accountList[count] = accountList[count+1];
    	    	}
    	    	System.out.println("Account number " + accountNumber + " is now permanently closed.");
    	    	result = true;
	    	}
    		else
    		{
    			System.out.println("No accounts was closed.");
    		}
	    	
    	}
    	return result;
    }

    // Gets the sum of the balances of all accounts in this bank.
    public double getTotalBalance()
    {
    	double totalBalance = 0;
    	for(int count = 0; count < numAccounts; ++count)
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
    public void countAccountsWithBalanceOverSpecifiedAmount()
    {
    	
    	double minAmount = readDouble("Enter the minimum amount.");
    	int counter = count(minAmount);
    	System.out.println("There are " + counter + " accounts with balances exceeding $" + minAmount);
    }

    //Finds a bank account with a given number.
    // Return the account with the given number, or null if there
    // is no such account.
    public BankAccount findAccount(int accountNumber)
    {
    	if(findAccountPosition(accountNumber) >= 0)
		{
    		return accountList[findAccountPosition(accountNumber)];
		}
    	else
    	{
    		return null;
    	}
    }

    public int findAccountPosition(int accountNumber)
    {
    	// The following is in the case that an account will be found
    	int position = 0;
    	while(/*accountList[position] != null &&*/ position < numAccounts)
    	{
    		//if(exists(accountNumber) && accountList[position].getAccountNumber() != accountNumber)
    		
    		if(accountList[position].getAccountNumber() == accountNumber) // If it finds it
    		{
    			break;
    		}
    		else if(position == numAccounts - 1)
    		{
    			position = -1;
    			break;
    		}
    		position++;
    	}
    	return (position);
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
    public boolean deposit(int accountNumber, double amount)
    {
    	boolean result;
    	if(exists(accountNumber))
    	{
    		accountList[findAccountPosition(accountNumber)].deposit(amount);
    		result = true;
    	}
    	else
    	{
    		System.out.println("Error in Bank deposit: account number " + accountNumber + " does not exist.");
    		result = false;
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

    public double getBalance(int accNum)
    {
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
    		return(closeAccount(readInt("Enter account number in the range [111, 999]:")));
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
                    countAccountsWithBalanceOverSpecifiedAmount();
                    break;
                case 'q':
                    quit();
            }
        } while (choice != 'q');
    }
}
```

_**Here is my BankAplication class (this is the driver code):**_
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
		System.out.print("Enter initial capacity of bank accounts: ");
		int capacity = kb.nextInt();
		Bank bank = new Bank(name, capacity);
		bank.run();
	}
}
```

**_Here is my BankAccount class (the bug is probably not here but just including this class so that the code doesn't look ambiguous):_**
```
public class BankAccount
{
   private String name;
   private int accountNumber;
   private double balance;
   public static final double MIN_BALANCE = 50;
   public static final int MIN_ID = 111;
   public static final int MAX_ID = 999;

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
   public static boolean isValidId(int id)
   {
	   if(id >= MIN_ID && id <= MAX_ID)
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
	   if(balance >= MIN_BALANCE)
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

I have a strong feeling that this is going to be the last problem I am going to encounter with this program, so if someone could please point out what the issue is then it would be GREATLY appreciated!

Thanks in advance!

---

### Post by Some Penguin on 2010-03-18
Think about the case where you're trying to close a non-existent account, and look at your code.   Consider what invariants exist before you do that, and what will change.  

Try stepping through it with a debugger if you don't see the problem.  Not to say that that is definitely the only problem, but there is a problem there.

---

### Post by s3a on 2010-03-19
Sorry for being stupid but I've been looking at it since you posted and when you say to look at me closing an account that does not exist, I focused on the following particularly on the bolded part. Are you saying I need to to do something other than just print an error message when trying to close an account that already exists or have I got it all wrong?

```
public boolean closeAccount(int accountNumber)
    {
    	boolean result = false;
    	int position = this.findAccountPosition(accountNumber);
    	[B]if( position == -1)
    	{
    		System.out.println("Account number " + accountNumber + " does not exist. No account closed.");
    	}[/B]
    	else
    	{
    		System.out.println("Your account is about to be closed.");
    		if(yesno("Are you sure you want to close (remove and discard) this account (y/n)?") == 'y')
	    	{
    			--numAccounts;
    	    	for(int count = position; count < numAccounts; count++)
    	    	{
    	    		accountList[count] = accountList[count+1];
    	    	}
    	    	System.out.println("Account number " + accountNumber + " is now permanently closed.");
    	    	result = true;
	    	}
    		else
    		{
    			System.out.println("No account was closed.");
    		}
	    	
    	}
    	return result;
    }
```

---

### Post by Some Penguin on 2010-03-19
Ah, misspoke.  Or, rather, mistyped.

Think:  it exists, but person says 'no', abort the cancel.

---

### Post by s3a on 2010-03-19
But it does abort the remove account request because it goes straight to the corresponding else clause and executes System.out.println("No account was closed.");

---

### Post by falconindy on 2010-03-20
I didn't compile this, but it seems to me that the problem is in the findAccountPosition method. Add some debugging statements and look at how long you spend in the while loop before exiting.

---

### Post by s3a on 2010-03-20
I think I solved this particular bug!

Here is what I changed:
```
public int findAccountPosition(int accountNumber)
    {
    	// The following is in the case that an account will be found
    	int position = 0;
    	while(/*accountList[position] != null &&*/ position < numAccounts)
    	{
    		//if(exists(accountNumber) && accountList[position].getAccountNumber() != accountNumber)
    		
    		if(accountList[position].getAccountNumber() == accountNumber) // If it finds it
    		{
**    			position--;**
    			break;
    		}
    		else if(position == (numAccounts - 1))
    		{
    			position = -1;
    			break;
    		}
    		position++;
    	}
    	return (position);
    	}
```

However, I have another bug that allows me to create more than one copy of the same account. I'll work on that now. And by the way, thanks.

---

### Post by falconindy on 2010-03-20
Not at all what I had in mind. Your new bug is likely related to your "solution" to this first one.

Step through your own logic inside the while loop. What happens if the account number you're trying to find isn't the first one encountered? Follow what happens in the else clause. Do you ever reach position++ outside the if/else?

---

### Post by s3a on 2010-03-20
It seems that I solved all my problems doing something other than what you suggested. Either that or I don't understand what you mean by "What happens if the account number you're trying to find isn't the first one encountered?" I did however realize that, like you said, the break statement gets out of the whole while loop and does not execute position++;

Am I correct? (So far I haven't encountered a bug - I bolded my changes or what I focused on basically):

```
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
    	boolean result;
    	if(exists(accountNumber) || numAccounts == accountList.length || BankAccount.isValidAccountNumber(accountNumber) == false || BankAccount.isValidBalance(initialBalance) == false)
    	{
    		result = false;
    	}
    	else
    	{
    		accountList[numAccounts] = new BankAccount(name, accountNumber, initialBalance);
    		++numAccounts;
    		result = true;
    	}
    	return result;
    }

    public boolean exists(int accNum)
    {
    	return  ( findAccount(accNum) != null );
    }

    // Close an account with a given number
    public boolean closeAccount(int accountNumber)
    {
    	boolean result = false;
    	int position = this.findAccountPosition(accountNumber);
    	if( position == -1)
    	{
    		System.out.println("Account number " + accountNumber + " does not exist. No account closed.");
    	}
    	else
    	{
    		System.out.println("Your account is about to be closed.");
    		if(yesno("Are you sure you want to close (remove and discard) this account (y/n)?") == 'y')
	    	{
    			--numAccounts;
    	    	for(int count = position; count < numAccounts; count++)
    	    	{
    	    		accountList[count] = accountList[count+1];
    	    	}
    	    	System.out.println("Account number " + accountNumber + " is now permanently closed.");
    	    	result = true;
	    	}
    		else
    		{
    			System.out.println("No account was closed.");
    		}
	    	
    	}
    	return result;
    }

    // Gets the sum of the balances of all accounts in this bank.
    public double getTotalBalance()
    {
    	double totalBalance = 0;
    	for(int count = 0; count < numAccounts; ++count)
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
    public void countAccountsWithBalanceOverSpecifiedAmount()
    {
    	
    	double minAmount = readDouble("Enter the minimum amount.");
    	int counter = count(minAmount);
    	System.out.println("There are " + counter + " accounts with balances exceeding $" + minAmount);
    }

    //Finds a bank account with a given number.
    // Return the account with the given number, or null if there
    // is no such account.
    public BankAccount findAccount(int accountNumber)
    {
    	if(findAccountPosition(accountNumber) >= 0)
		{
    		return accountList[findAccountPosition(accountNumber)];
		}
    	else
    	{
    		return null;
    	}
    }

    public int findAccountPosition(int accountNumber)
    {
    	// The following is in the case that an account will be found
    	int position = 0;
    	[B]while(/*accountList[position] != null &&*/ position < numAccounts)
    	{
    		//if(exists(accountNumber) && accountList[position].getAccountNumber() != accountNumber)
    		
    		if(accountList[position].getAccountNumber() == accountNumber) // If it finds it
    		{
    			//position--; (breaks out of the WHOLE while loop)
    			break;
    		}
    		else if(position == (numAccounts - 1))
    		{
    			position = -1;
    			break;
    		}
    		position++;
    	}
    	return (position);[/B]
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
    public boolean deposit(int accountNumber, double amount)
    {
    	boolean result;
    	if(exists(accountNumber))
    	{
    		accountList[findAccountPosition(accountNumber)].deposit(amount);
    		result = true;
    	}
    	else
    	{
    		System.out.println("Error in Bank deposit: account number " + accountNumber + " does not exist.");
    		result = false;
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

    public double getBalance(int accNum)
    {
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
    
    [B]private void openNewBankAccount()
    {
        if (isFull())
        {
            System.out.println("Bank full - no room for more bank accounts");
            return;
        }
        else // Needs to be looked over a bit but I am on the right track
        {
        	int id = readAccountNumber();
        	if(exists(id))
        	{
        		System.out.println("That account already exists.");
        		return;
            }
        	else // If that account doesn't exist, create a new one
        	{
        		double amount = readBalance();
	            String ownername = getString("Enter owner's name: ");
	            openAccount(ownername, id, amount);
	            return;
        	}
        }[/B]
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
    		return(closeAccount(readInt("Enter account number in the range [111, 999]:")));
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
    	int accountNumber = readInt("Enter the account number to view its record: ");
    	if(exists(accountNumber))
    	{
//    		System.out.println(findAccount(accountNumber));
    		
    		double balance = findAccount(accountNumber).getBalance();
    		String name = findAccount(accountNumber).getName();
    		String str1 = "ID";
    		String str2 = "Balance";
    		String str3 = "Name";
    		System.out.printf("%10s\t%10s\t%10s\n", str1, str2, str3);
    		System.out.printf("%10d\t%8.2f\t%10s", accountNumber, balance, name);
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
                    System.out.println(this); // What's "this?"
                    break;
                case 's':
                    showBankRecord();
                    break;
                case 't':
                    totalAllAccountBalanceAmounts();
                    break;
                case 'k':
                    countAccountsWithBalanceOverSpecifiedAmount();
                    break;
                case 'q':
                    quit();
            }
        } while (choice != 'q');
    }
}
```

---

### Post by falconindy on 2010-03-20
No, your logic is still wrong.

Consider these structured english directions to iterating over an array, starting at index 0:

1) is index less than the size of the array?
  a) if no, **return** (some bad value)
  b) if yes, continue on
2) get value at index
3) compare value at index with value we're looking for
4) are they equal?
  a) If yes, **return** the index
  b) If no, continue on.
5) increment the index
6) repeat the process

How would one implement this in Java? Is this the same as what your code currently does? 

Also, a while loop isn't wrong in this case, but the problem may become clearer if you use a for loop instead.

edit: i compiled your code and ran through it. there's other problems than your find method which i don't have time to hunt down for you.

---

### Post by s3a on 2010-03-20
Oh wait! I hope I'm not wrong again :( ... but, is it because the else if will never be accessed because the while loop's condition is position < numAccounts ?

---

### Post by falconindy on 2010-03-20
Actually, you're okay. I misread the else/if part myself (oops).

Start adding debug statements. Something as simple as "hello from function x" can be helpful when troubleshooting because it gives you some insight into where your currently are within your program.

---

### Post by s3a on 2010-03-20
Oops on my part too again, the else CAN be accessed. The way I have my code, it works all the way until page 15/17 of my sample run that my teacher gave us. It says that account 777 exists already when I never actually created it. I'll post the user interaction soon, I just have to re-interact with it :(.

[U]Edit:
Here is the user interaction (the error is at the end if you don't want to read the whole thing):[/U]

```
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

    ID   balance  Name
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
Enter account number in the range [111, 999]: 111
Enter an initial balance ( >= 50.0 ) : 100.0
Enter owner's name: One Une

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
Enter account number in the range [111, 999]: 222
Enter an initial balance ( >= 50.0 ) : 200.0
Enter owner's name: Twenty Two

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
Enter owner's name: Forty Four

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

    ID   balance  Name
    ==================
    111   100.0   One Une
    222   200.0   Twenty Two
    444   400.0   Forty Four
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
Error in Bank deposit: account number 123 does not exist.

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

    ID   balance  Name
    ==================
    111   250.0   One Une
    222   200.0   Twenty Two
    444   400.0   Forty Four
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
Enter owner's name: Thirty Three

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
Enter owner's name: Fifty Five

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

    ID   balance  Name
    ==================
    111   250.0   One Une
    222   200.0   Twenty Two
    444   400.0   Forty Four
    333   300.0   Thirty Three
    555   500.5   Fifty Five
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
Enter account number in the range [111, 999]:321
Account number 321 does not exist. No account closed.

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
Enter account number in the range [111, 999]:444
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 444 is now permanently closed.

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

    ID   balance  Name
    ==================
    111   250.0   One Une
    222   200.0   Twenty Two
    333   300.0   Thirty Three
    555   500.5   Fifty Five
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
Total balance: 1250.5

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
Enter an initial balance ( >= 50.0 ): 260.0
There are 2 accounts with balances exceeding $260.0

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

    ID   balance  Name
    ==================
    111   250.0   One Une
    222   200.0   Twenty Two
    333   300.0   Thirty Three
    555   344.95   Fifty Five
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
Enter account number in the range [111, 999]:222
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?x
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 222 is now permanently closed.

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

    ID   balance  Name
    ==================
    111   250.0   One Une
    333   300.0   Thirty Three
    555   344.95   Fifty Five
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
Enter account number in the range [111, 999]:111
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 111 is now permanently closed.

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

    ID   balance  Name
    ==================
    333   300.0   Thirty Three
    555   344.95   Fifty Five
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
Enter account number in the range [111, 999]:555
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 555 is now permanently closed.

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

    ID   balance  Name
    ==================
    333   300.0   Thirty Three
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
Enter account number in the range [111, 999]:111
Account number 111 does not exist. No account closed.

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

    ID   balance  Name
    ==================
    333   300.0   Thirty Three
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

    ID   balance  Name
    ==================
    333   330.33   Thirty Three
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
Enter account number in the range [111, 999]:333
Your account is about to be closed.
Are you sure you want to close (remove and discard) this account (y/n)?y
Account number 333 is now permanently closed.

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

    ID   balance  Name
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
[B]Enter your choice: o
Enter account number in the range [111, 999]: 777
That account already exists.
[/B]
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
Enter your choice: 
```

_Edit #2:_
After posting "Edit(#1)," I even decided to ask it to print (by pressing p) and it printed that there were 0 accounts open and that was right after it said account 777 already existed.

After that, I wanted to see what it had:
```
Enter your choice: s
Enter the account number to view its record: 777
        ID	   Balance	      Name
       777	  330.33	Thirty Three
```

... it has the contents of the 333 account. How did that happen!?

---

### Post by dwhitney67 on 2010-03-21
You have a bug (and poor indentation) in the code below:
```

    public int findAccountPosition(int accountNumber)
    {
    	// The following is in the case that an account will be found
    	int position = 0;
    	while(/*accountList[position] != null &&*/ position < numAccounts)
    	{
    		//if(exists(accountNumber) && accountList[position].getAccountNumber() != accountNumber)
    		
    		if(accountList[position].getAccountNumber() == accountNumber) // If it finds it
    		{
    			//position--; (breaks out of the WHOLE while loop)
    			break;
    		}
    		else if(position == (numAccounts - 1))
    		{
    			position = -1;
    			break;
    		}
    		position++;
    	}
    	return (position);
    	}

```
Ask yourself... what is the value of 'numAccounts' when there are no accounts open?  Then ask yourself, what will the function above return when you query whether an account with an ID of '777' exists?

Will it be -1 (the desired value), or will it be 0 (zero), or some other value?

P.S.  Clean up the code above to remove the fluff that is not really needed.  Initially, assume the bank account does not exist, until proven otherwise.

---

### Post by s3a on 2010-03-21
Does this code address the issue(s)?

```
public int findAccountPosition(int accountNumber)
    {
    	// The following is in the case that an account will be found
    	int position = 0;
    	
    	if(numAccounts != 0)do
    	{	
    		if(accountList[position].getAccountNumber() == accountNumber) // If it finds it
    		{
    			break;
    		}
    		else if(position == (numAccounts - 1))
    		{
    			position = -1;
    			break;
    		}
    		position++;
    	}while(position < numAccounts);
    	
    	if(numAccounts == 0) position = -1;
    	return (position);
    	}
```

Edit: It seems that it does! I went through the 17 pages of the sample run pdf my teacher gave me and I have no bugs! I just need to fix some minor cosmetic stuff and something. The something else is:

[B]The Vanier banking system is now shutting down . . .
_BUILD SUCCESSFUL (total time: 12 minutes 42 seconds)_
The Vanier banking system is now shutting down . . .[/B]

The underlined part is what I don't have. Basically, how do I make Java count how long the user session lasted?

---

### Post by dwhitney67 on 2010-03-21
Like I suggested earlier, cut the "fluff" out of the code:
```

public int findAccountPosition(int accountNumber)
{
   int position = -1;   // assume the account does NOT exist

   for (int n = 0; n < numAccounts; ++n)
   {
      if (accountList[n].getAccountNumber() == accountNumber)
      {
         position = n;
         break;
      }
   }

   return position;
}

```

---

### Post by falconindy on 2010-03-21
> **s3a said:**
> [B]The Vanier banking system is now shutting down . . .
_BUILD SUCCESSFUL (total time: 12 minutes 42 seconds)_
The Vanier banking system is now shutting down . . .[/B]

The underlined part is what I don't have. Basically, how do I make Java count how long the user session lasted?

[This](http://java.sun.com/j2se/1.4.2/docs/api/java/lang/System.html#currentTimeMillis()) should do what you want.

---

### Post by Can+~ on 2010-03-21
Also:

[PHP]        if(accountList.length == numAccounts)
        {
        	return true;
        }
        else
        {
        	return false;
        }
[/PHP]

Can be rewritten as:

[PHP]return (accountList.length == numAccounts);[/PHP]

Too bad I don't have a Java compiler to test that, but it should work.

---

### Post by s3a on 2010-03-21
Thanks to all of you! By the way, Can+~, since you made me realize that more efficient way to code the isFull() method, I did the same for the isEmpty() method "return (numAccounts == 0);"

I have one more question now and it's not about a bug this time :)! It's just when I press "p" during user interaction and it runs "System.out.println(this);"...what is "this" "carrying" or "holding" if you know what I mean for System.out.println() to print? (because I want to make "balance" be "Balance" which is a very minor cosmetic thing but I'd like to know how)

---

### Post by dwhitney67 on 2010-03-21
> **s3a said:**
> Thanks to all of you! 
You're welcome.

> **s3a said:**
> 
I have one more question now and it's not about a bug this time :)! It's just when I press "p" during user interaction and it runs "System.out.println(this);"...what is this "carrying" or "holding" if you know what I mean for System.out.println() to print? (because I want to make "balance" be "Balance" which is a very minor cosmetic thing but I'd like to know how)

Please rephrase the above in English.


P.S.  IMO, a priority on your list is to display monetary values in the appropriate form for the locale in which the bank is located.  So instead of $1.5 (for a dollar-fifty), you would display $1.50.

---

### Post by s3a on 2010-03-21
I already addressed the decimal issue. That's part of what I meant by "cosmetic things."

As for rephrasing, System.out.println(**this**); What is **this**? Like, I know that it's the calling object or something like that but, in this case, how do I know which object it is?

Or basically; how does **System.out.println(this);** know what to print?

Edit: I just fixed the lowercase b to capital B but I'd still like to know the answer to that question.

---

### Post by falconindy on 2010-03-21
Whatever class "this" appears in is what it refers to. For example...

```
public class Account {
  private int acctNumber;
  private String custName;

  public Account(int acctNumber, String custName) {
    this.acctNumber = acctNumber;
    this.custName = custName;
    System.out.println(this);
  }

  public String toString() {
    return acctNumber + " is owned by " + custName;
  }
}
```
There's two things going on here with the 'this' keyword. First, I'm using it to differentiate between the instance variables and the parameters passed to the constructor. Second, System.out.println is called on 'this'. Not sure if you've come across this yet: If you pass an object to a print method, it'll invoke the toString method of the object. So in this case, after the object is constructed, you'll see something like "123456 is owned by Bob". You can still print an object's string representation even if toString doesn't explicitly exist in the class, but that's a whole different topic.

---

### Post by s3a on 2010-03-24
Yes, my teacher covered that. So, in your example, if I didn't override the toString() method, would it just print "123456Bob" instead of "123456 is owned by Bob" or what would happen exactly?

---

### Post by dwhitney67 on 2010-03-24
> **s3a said:**
> Yes, my teacher covered that. So, in your example, if I didn't override the toString() method, would it just print "123456Bob" instead of "123456 is owned by Bob" or what would happen exactly?
This is the type of question that would take you only a couple of minutes, if not less, to discover for yourself the answer, by merely writing a few lines of code.

---

### Post by falconindy on 2010-03-24
> **dwhitney67 said:**
> This is the type of question that would take you only a couple of minutes, if not less, to discover for yourself the answer, by merely writing a few lines of code.
Or just look in the source files included with Java to see that the toString method returns a string based on the class name and hashCode of the object.

BUT WAIT, WOTS A HASHCODE?!

---

