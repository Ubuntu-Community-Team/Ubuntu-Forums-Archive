---
title: "JAVA Banking desperate help!"
date: 2009-01-14
forum: Programming Talk
---

### Post by JoCoProductions on 2009-01-14
Hey guys I'm trying to program a simple ATM machine, and I decided to get all fancy and try out a UI (we haven't even gotten to Arrays yet). Needless to say I got stuck pretty quickly.

The problem I'm having is I need to be able to check whether the user input in the JTextField matches one of the accounts. I set up a method in another class checkLogin to check the login. When I called on it in the UI and driver class it results in an error "non-static method checkLogin cannot be referenced from a static context".

Heres my code:
```
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;

public class ATMLogin extends JFrame implements ActionListener
{ 
    private JTextField user;
    private JTextField pass;
    private JButton enter;
    private JLabel lblstat; 

    public static void main(String[] args)
    {
        ATMLogin frame = new ATMLogin();
        
        frame.setTitle("Computer Science National ATM Login");
        frame.setVisible(true);
        frame.setDefaultCloseOperation(EXIT_ON_CLOSE);
        frame.setResizable(false);
        frame.pack();
    }
    
    public ATMLogin()
    {
        JPanel ATM = new JPanel();
        
        ATM.setLayout(new GridLayout(4, 2, 5, 5));
        ATM.setBorder(BorderFactory.createTitledBorder("Computer Science National ATM Login"));
        
        JLabel lbluser = new JLabel ("Name: ");
        JLabel lblpass = new JLabel("Password: ");
        
        user = new JTextField();
        user.addActionListener(this);
        
        pass = new JTextField();
        pass.addActionListener(this);
        
        enter = new JButton("Enter");
        enter.addActionListener(this);
        
        JLabel space = new JLabel("");
        
        JLabel lblauth = new JLabel("Authorization");
        lblstat = new JLabel("");
        
        ATM.add(lbluser);
        ATM.add(user);
        ATM.add(lblpass);
        ATM.add(pass);
        ATM.add(space);
        ATM.add(enter);
        ATM.add(lblauth);
        ATM.add(lblstat);

        add(ATM);
    }
              
             
    public void actionPerformed(ActionEvent e)    
    { 
        if(e.getSource() == enter)
        {
            String input1 = user.getText();
            String input2 = pass.getText();
                                 
            Account.checkLogin("input1", "input2");
            
            if (true)
            {
                lblstat.setForeground(Color.GREEN);
                lblstat.setText("Successful");
            }
            else
            {
                lblstat.setForeground(Color.RED);
                lblstat.setText("Failed");
            }
                     
           
        }
    }
}
```

Methods:
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
   public Account (String owner, String pass, int account, double initial)
   {
      name = owner;
      acctNumber = account;
      balance = initial;
      password = pass;
   }
   
   public boolean checkLogin (String input1, String input2)
   {    
       if(input1 == name && input2 == password)
       {
            return true;
        } 
        else
        {
            return false;
        }
    }
```

---

### Post by slavik on 2009-01-14
Can you give us the exact error message? (It should include a line number)

Also, the following does not do what you think it does.
```

            Account.checkLogin("input1", "input2");
            
            if (true)

```

---

### Post by JoCoProductions on 2009-01-14
> non-static method checkLogin(java.lang.String,java.lang.String) cannot be referenced from a static context

I have successfully compiled everything but when I add the line ```
Account.checkLogin("input1", "input2");
``` it doesnt compile and instead gives me that error. 

Is there another way to check the user inputted name and password against what i have in my database? How would you write it?

---

### Post by eye208 on 2009-01-14
The difference between static and non-static members is that the former exist only once and are shared by all instances of the class. Non-static members exist separately for each instance.

In your example, you are calling the method like this:
```
Account.checkLogin("input1", "input2");
```
"Account" is not an object of type Account but the class name itself. You can only access static members this way. However, the method "checkLogin()" is non-static. If it was static, it would be unable to access the non-static members "name" and "password". If "name" and "password" were static too, these would be shared among all accounts, so that's probably not what you want to do anyway.

Wait until you have learned about arrays, so you can build an ATM machine for more than just one account. ;)

By the way, the quotes around "input1" and "input2" are wrong too. You are passing string literals instead of string variables. But this is not what is causing the compilation errors.

---

### Post by slavik on 2009-01-14
I see now ... you can't do that.

you have to create an object of an account type and then call the checklogin, so something like the following:
```

Account acc = new Account();
acc.checkLogic(....);

```

You are calling Account as an object, but it isn't, it is a class. Do you completely understand the difference between an object and a class?

---

### Post by JoCoProductions on 2009-01-14
I think I understand the difference, I understand exactly what you're saying. The problem is that I have 5 accounts (acct1, acct2, acct3, acct4, acct5) and the user is the one that gets to choose which one gets called. So if I were to write acct1.checkLogin() it would only be a viable solution for that account. I need it so that if the user-entered name/password matches any of the accounts it logs into that specific account.

---

### Post by eye208 on 2009-01-14
> **JoCoProductions said:**
> The problem is that I have 5 accounts (acct1, acct2, acct3, acct4, acct5) and the user is the one that gets to choose which one gets called. So if I were to write acct1.checkLogin() it would only be a viable solution for that account.
That's why you need arrays (or something similar, like a vector for example), so you can store all accounts in one object. Then you can use a loop construct to iterate through the list of accounts and find the one with the matching user/password combination.

---

### Post by JoCoProductions on 2009-01-14
It seems I may have gotten in over my head. I'm not quite that advanced yet, but that's all a part of learning. So is this the only way this can be possible, through an array or somthing similar?

---

### Post by trivialpackets on 2009-01-14
I don't know java, but my first thought would be a change in the design.  Rather than having the checklogic within the account, have it within another class of..I don't know Customer or something, and then link the customer to the specific accounts.  So the login is handled by the object of type customer, and only that customer has access to his accounts.  Although, that will likely include an array of some sort as well unless you were working with a database...

---

### Post by eye208 on 2009-01-14
> **JoCoProductions said:**
> So is this the only way this can be possible, through an array or somthing similar?
It's the only way that makes sense. Imagine a list of, say, 100 accounts. You don't want to assign each of these to a separate variable, and then write 100 calls to checkLogin() into your program. And then modify the code for each additional account. With an array you can do it like this:
```
for (int i = 0; i < acct.length; i++)
    if (acct[i].checkLogin()) { /* do something */ }
```
Take your time. You will learn about these things soon enough. ;)

---

### Post by JoCoProductions on 2009-01-14
Alright, I'm on the right track now....

Thanks so much you guys for the quick help, you really me out a lot!

---

### Post by jespdj on 2009-01-14
You're incorrectly comparing strings with ==, you should use equals().

See [your other thread](http://ubuntuforums.org/showthread.php?t=1039393), where I explained it in more detail.

---

