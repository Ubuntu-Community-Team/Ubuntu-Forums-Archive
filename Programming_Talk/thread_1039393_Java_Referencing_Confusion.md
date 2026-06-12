---
title: "Java Referencing Confusion"
date: 2009-01-14
forum: Programming Talk
---

### Post by JoCoProductions on 2009-01-14
Hey guys I'm trying to create an ATM application. I have two main classes and I'm a little stuck. One of my classes contains almost all the methods, while the other is the driver and contains the UI elements. In my methods class I defined an Acount object. In the driver class I have specified Accounts (acct1, acct2...). What I am trying to do is have a user-inputted login and the program checks against the accts in the database to see if the login is correct. My boolean checkLogin method keeps returning false, even though it is clearly correct. Snippets of my code:

```
 public void actionPerformed(ActionEvent e)    
    { 
        if(e.getSource() == enter)
        {
            Account acct1, acct2, acct3, acct4;
       
            acct1 = new Account("Kevin Rose", "1111", 72354, 102.56);
            acct2 = new Account("Senior Twiet", "2222", 69713, 40.00);
            acct3 = new Account("Kelsey Farman", "3333", 93757, 469.32);
            acct4 = new Account("Joey Cody", "4444", 13375, 875.00);
       
            String input1 = user.getText();
            String input2 = pass.getText();
                                          
                       
            if (acct1.checkLogin(input1, input2) == true)                      
                new Menu();          
            else
                 if (acct2.checkLogin(input1, input2) == true)
                        new Menu();
                    else
                        if (acct3.checkLogin(input1, input2) == true)
                                new Menu();
                            else   
                                if (acct4.checkLogin(input1, input2) ==true)
                                        new Menu();
                                    else         
                                            lblstat.setForeground(Color.RED);
                                            lblstat.setText("Incorrect Login");
```

```
public class Account
{
   private NumberFormat fmt = NumberFormat.getCurrencyInstance();

   private final double RATE = 0.035;  // interest rate of 3.5%
   private final double fee = 1.50;

   private long acctNumber;
   private double balance;
   private String password;
   private String name;
     
   //-----------------------------------------------------------------
   //  Sets up the account by defining its owner, account number,
   //  and initial balance.
   //-----------------------------------------------------------------
   public Account (String owner, String pass, long account, double initial)
   {
      name = owner;
      password = pass;
      acctNumber = account;
      balance = initial;     
   }
   
   public boolean checkLogin (String input1, String input2)
   {    
        if (input1 == name && input2 == password)
                return true;
        else {
            System.out.println(input1 + " " + name + " " + input2 + " " + password);
            return false;
            }
    }
```

On the else statement on that last one that keeps returning false I added that println to see what could be wrong.

```
Kevin Rose Kevin Rose 1111 1111
Kevin Rose Senior Twiet 1111 2222
Kevin Rose Kelsey Farman 1111 3333
Kevin Rose Joey Cody 1111 4444

```
It looks right to me, the input1 & name and input2 & password match. Why the hell am I having so much trouble???

---

### Post by jespdj on 2009-01-14
You should not compare String objects with the == operator in Java. Use equals() instead:
```

public boolean checkLogin (String input1, String input2)
   {    
        if (input1.equals(name) && input2.equals(password))
                return true;
        else {
            System.out.println(input1 + " " + name + " " + input2 + " " + password);
            return false;
            }
    }

```
In Java, the == operator checks if both arguments are referring to the same object - not if the content of the objects is the same.

Note, you should not use "== true" in your if-statements; that's unnecessary. Simply remove the "== true", for example:
```

if (acct1.checkLogin(input1, input2))

```

p.s. Why didn't you continue in [your other thread](http://ubuntuforums.org/showthread.php?t=1039096)?

---

### Post by JoCoProductions on 2009-01-14
I knew I was right on it! Thank you sooooooo much jespdj! I'm just learning and I was looking at that problem for over 2 hours lol. I honestly can't tell you how relieved I am, THANK YOU!

---

