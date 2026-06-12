---
title: "(Java) Something in my equals method is causing a syntax error"
date: 2010-02-01
forum: Programming Talk
---

### Post by s3a on 2010-02-01
Here is my code:
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
	public BankAccount(String name, int id, double balance)
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
[B]	public boolean equals(Object obj) // Check
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
		boolean haveSameBalance  = this.getBalance() == obj.getBalance();
		boolean haveSameAccount = this.getAccountNumber() == obj.getAccountNumber();

		if(haveSameName == true && haveSameBalance == true && haveSameAccount == true)
			result = true;
		else
			result = false;
		return result;[/B]
```

and here is the syntax error message provided by the compiler:
```
javac BankAccount.java
BankAccount.java:85: cannot find symbol
symbol  : method getBalance()
location: class java.lang.Object
		boolean haveSameBalance  = this.getBalance() == obj.getBalance();
		                                                   ^
BankAccount.java:86: cannot find symbol
symbol  : method getAccountNumber()
location: class java.lang.Object
		boolean haveSameAccount = this.getAccountNumber() == obj.getAccountNumber();
		                                                        ^
2 errors
```

Could someone please help me identify the culprit here?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2010-02-01
POC (piece of cake)... your 'obj' is an Object; not a *BankAccount* object.  Cast first, or use the *bankAccount* handle, then call getBalance().

P.S.  I never quite understood why an equals() method would take an Object.  Why not just declare the parameter to be a BankAccount type?  That would prevent someone from passing an extraneous object (eg. Circle).  It would also mitigate the need to check if the object type is BankAccount.

---

### Post by s3a on 2010-02-01
I don't understand what you're saying. I tried copying the
**BankAccount bankAccount = (BankAccount)obj;**
statement on top of my first if statement and below the beginning of the equals method but that still gives me syntax errors.

As for your question, I think the answer is that if you declare the parameter as a BankAccount type, you won't be able to return false to indicate to the user that they are not equal? I don't know if I'm correct or saying stupidities but that's what I think.

---

### Post by PaulM1985 on 2010-02-01
After doing the cast did you make the changes elsewhere.  Eg instead of using obj.SomeMethod() you are now using bankAccount.SomeMethod().  Are you using the bankAccount variable instead of the obj variable in the tests?

Paul

These lines:

		boolean haveSameBalance  = this.getBalance() == obj.getBalance();
		boolean haveSameAccount = this.getAccountNumber() == obj.getAccountNumber();

need to be changed to use bankAccount rather than obj.

---

### Post by Some Penguin on 2010-02-01
> **s3a said:**
> Here is my code:
```
public class BankAccount

{
    private String name;
    private int accountNumber;
    private double balance;

// Consider testing for null name.  -- SP
    public BankAccount(String name, int accountNumber)
    {
        this.name = name;
        this.accountNumber = accountNumber;
        balance = 0.0;
    }
    public BankAccount(String name, int id, double balance)
    {
        this.name = name;
        this.accountNumber = accountNumber;
        this.balance = balance;
    }

```
Did you mean 'id' instead of accountNumber in the assignment?


    private void setBalance(double balance)
    {
        this.balance = balance;
    }
[/code][/quote]

Fairly strange that this is private.

> ```

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
[quote][code]
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

```

It probably doesn't much matter in this particular case, but Double.compare() exists for some pretty good reasons.

> ```

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

```
s/idt/it/

    public String toString() // Check
    {
        String str = "Name: " + name + "\nAccount Number: " + accountNumber + "\nBalance: " + balance;
        return str;
    }
[/code][/quote]

Adding my comments inline in the next section.

> ```

[B]    public boolean equals(Object obj) // Check
    {
        if(this == obj)
            return true;
        if(obj == null)
            return false;

      // Use equals() below.   Or the more traditional instanceOf.
        if(this.getClass() != obj.getClass())
            return false;

        boolean result;
        BankAccount bankAccount = (BankAccount)obj;

// NullPointerException if name is null. -- SP
        boolean haveSameName  = this.getName().equals(bankAccount.getName());

       /* Use Double.compare().  And parenthesis.  
            And use bankAccount instead of obj.  
           And also, you don't need to keep going if any of these tests fail. -- SP
        */
        boolean haveSameBalance  = this.getBalance() == obj.getBalance();
        boolean haveSameAccount = this.getAccountNumber() == obj.getAccountNumber();

        // You don't need the == true bits.  -- SP
        if(haveSameName == true && haveSameBalance == true && haveSameAccount == true)
            result = true;
        else
            result = false;
        return result;[/B]
```

and here is the syntax error message provided by the compiler:
```
javac BankAccount.java
BankAccount.java:85: cannot find symbol
symbol  : method getBalance()
location: class java.lang.Object
        boolean haveSameBalance  = this.getBalance() == obj.getBalance();
                                                           ^
BankAccount.java:86: cannot find symbol
symbol  : method getAccountNumber()
location: class java.lang.Object
        boolean haveSameAccount = this.getAccountNumber() == obj.getAccountNumber();
                                                                ^
2 errors
```Could someone please help me identify the culprit here?

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by dwhitney67 on 2010-02-01
Sigh...

```

public boolean equals(Object obj)
{
   ...

   BankAccount bankAccount = (BankAccount)obj;

   ...

   boolean haveSameBalance = this.getBalance() == **bankAccount**.getBalance();
   boolean haveSameAccount = this.getAccountNumber() == **bankAccount**.getAccountNumber();

   ...
}

```
You cannot use obj above in the conditional statements.  obj is an Object class; it does not have awareness of the getBalance() or getAccountNumber() methods.  That is why it is necessary to cast it to the appropriate object type (BankAccount) *and then* access the methods.

P.S.  Rather than create temporary booleans, just put all of the conditional together into one statement:
```

return this.getAccountName().equals(bankAccount.getAccountName()) &&
       this.getAccountBalance() == bankAccount.getAccountBalance() &&
       this.getAccountNumber() == bankAccount.getAccountNumber();

```

---

