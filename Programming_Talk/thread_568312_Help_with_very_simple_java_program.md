---
title: "Help with very simple java program"
date: 2007-10-05
forum: Programming Talk
---

### Post by thursgun on 2007-10-05
These are the codes:

```
public class Account 
{
        protected double balance;

        // Constructor to initialize balance
        public Account( double amount )
	{
		balance = amount;
	}

        // Overloaded constructor for empty balance
        public Account()
	{
		balance = 0.0;
	}

        public void deposit( double amount )
	{
		balance += amount;
	}

        public double withdraw( double amount )
	{
                // See if amount can be withdrawn
		if (balance >= amount)
		{
			balance -= amount;
                        return amount;
		}
		else
                // Withdrawal not allowed
                        return 0.0;
	}

        public double getbalance()
	{
                return balance;
	}
}
```

```
class AccountDemo 
{
        public static void main(String args[])
	{
                // Create an empty account
                Account my_account = new Account();

                // Deposit money
		my_account.deposit(250.00);

                // Print current balance
		System.out.println ("Current balance " +
			my_account.getbalance());

                // Withdraw money
		my_account.withdraw(80.00);

                // Print remaining balance
		System.out.println ("Remaining balance " +
			my_account.getbalance());
	}
}
```

I can compile the first one, but the AccountDemo doesn't.

I get the following error:
```
----------
1. ERROR in AccountDemo.java (at line 6)
        Account my_account = new Account();
        ^^^^^^^
Account cannot be resolved to a type
----------
2. ERROR in AccountDemo.java (at line 6)
        Account my_account = new Account();
                                 ^^^^^^^
Account cannot be resolved to a type
----------
2 problems (2 errors)
```

I'm using JDK (javac). I previously used gcj.

---

### Post by aks44 on 2007-10-05
Hmm I'm not an expert at Java, but from what I remember you need to **import whatever.class.path.Account** in AccountDemo to be able to use the Account class.

Hope this helps, although it's been long time I've written any Java code... (if I made a syntax mistake, maybe someone can correct me?)

---

### Post by thursgun on 2007-10-05
mmm, how exactly i do that?

I was told that I must create a package....

---

### Post by Celegorm on 2007-10-05
It compiles fine for me. Are the two files in the same directory? Are they named Account.java and AccountDemo.java? What command are you using to compile it?

---

### Post by thursgun on 2007-10-05
Yes, and yes.

I'm using:

~$: javac Account.java

When I do  ~$: java Account i get the following error:
Exception in thread "main" java.lang.NoSuchMethodError: main

---

### Post by Celegorm on 2007-10-05
Did you update the java alternatives when you switched to JDK from gcj? If not there's a guide on how to do that [here]("http://ubuntuforums.org/showthread.php?t=201378")

---

### Post by thursgun on 2007-10-05
It worked!
I needed to update the java alternatives.

Thank you so much!

---

### Post by Celegorm on 2007-10-05
Glad it worked :) Took me a couple hours to figure out I needed to do that the first time I tried to compile a java program in Ubuntu ](*,)

---

