---
title: "&lt;identifier&gt; expected error java"
date: 2008-03-10
forum: Programming Talk
---

### Post by chelfc on 2008-03-10
Hi guys,  I have this code and when I try to compile and run it gives me an <identifier> expected error.

The code with the irrelevant parts taken out.

```


package ACCOUNT;

import java.util.Scanner;
import java.util.GregorianCalendar;
import javax.swing.*;

class Bank{

static private double bal;   //Account balance
static int withdraw;      //amount of times withdrawn 

static void setBal(double amount){bal = amount;}
static double getBal(){return bal;}

public static void main(String[] args){
//code
}

class Charge extends Bank{
  
double fee = Bank.withdraw * 0.10;
double tempbal = Bank.getBal();
double amount = tempbal - fee ;
Bank.setBal(amount);
    }

```

when I run it points to the line Bank.setBal(amount) and says <identifier> expected

can someone help?

---

### Post by mike_g on 2008-03-10
You want to use:
```
this.setBal(amount);
```
Or just:
```
setBal(amount);
```

Edit: I dont really see much of a point creating a charge class that inherits the bank. IMHO it would make more sense to add a charge function to the bank class instead and pass a fee in from elsewhere.

---

### Post by chelfc on 2008-03-10
i know, but thats what I was told to do, it is for an assignment. I'm basically done though, it is just this error message that appears. I have to create two subclasses classes (another one being the superclass), each one accessing the balance and subtracting the relevant fee.  one of the classes you are not seeing, as it accesses the balance the same way and the same error appears.

---

### Post by chelfc on 2008-03-10
> **mike_g said:**
> You want to use:
```
this.setBal(amount);
```
Or just:
```
setBal(amount);
```

Edit: I dont really see much of a point creating a charge class that inherits the bank. IMHO it would make more sense to add a charge function to the bank class instead and pass a fee in from elsewhere.

also, what do you mean this.setBal(amount), isn't "this" supposed to be Bank?

---

### Post by chelfc on 2008-03-10
I tried removing the private part from the variable declaration. removed the method to access the balance, since it was no longer needed and could just be accessed from the subclass using bank.bal. but it still gives me the identifier error on the line I access the bal from in the subclass

---

### Post by Zugzwang on 2008-03-11
Of course it does not work. It's mainly because your "Bank.setBal(amount);" statement is not part of a method. Therefore the compiler thinks that you want to declare some variable, but Bank.setBal is no such type.

There's another error: You don't have enough closing braces. If you use your favourite editor to format your code, you obtain:

[PHP]
import java.util.Scanner;
import java.util.GregorianCalendar;
import javax.swing.*;

class Bank{
    
    static private double bal;   //Account balance
    static int withdraw;      //amount of times withdrawn
    
    static void setBal(double amount){bal = amount;}
    static double getBal(){return bal;}
    
    public static void main(String[] args){
        //code
    }
    
    class Charge extends Bank{
        
        double fee = Bank.withdraw * 0.10;
        double tempbal = Bank.getBal();
        double amount = tempbal - fee ;
        Bank.setBal(amount);
    }
[/PHP]

Looks incorrect, doesn't it? There's a closing brace missing after the main function. So this is far better (note that I dropped your package command. It is convention to use lower-case package names anyway):

[PHP]
import java.util.Scanner;
import java.util.GregorianCalendar;
import javax.swing.*;

class Bank{
    
    static private double bal;   //Account balance
    static int withdraw;      //amount of times withdrawn
    
    static void setBal(double amount){bal = amount;}
    static double getBal(){return bal;}
    
    public static void main(String[] args){
        //code
    }
}

class Charge extends Bank{
    
    double fee = Bank.withdraw * 0.10;
    double tempbal = Bank.getBal();
    double amount = tempbal - fee ;
    Bank.setBal(amount);
}[/PHP]

Ok, but there's still this error. The point is that if you want to call functions at the loading time of the class, you need to add a static block (as already mentioned, your code is a little bit confusing anyway). So you get:

[PHP]
import java.util.Scanner;
import java.util.GregorianCalendar;
import javax.swing.*;

class Bank{
    
    static private double bal;   //Account balance
    static int withdraw;      //amount of times withdrawn
    
    static void setBal(double amount){bal = amount;}
    static double getBal(){return bal;}
    
    public static void main(String[] args){
        //code
    }
}

class Charge extends Bank{
    
    double fee = Bank.withdraw * 0.10;
    double tempbal = Bank.getBal();
    double amount = tempbal - fee ;
    static {
        Bank.setBal(amount);
    }
}
[/PHP]

Uuuh, but this still doesn't compile since "amount" isn't static. Hmm, so you have two options:
[LIST]
[*]Making the "fee", "tempbal" and "amount" static as well
[*]putting the "setBal" somewhere else, e.g. in the constructor of Charge
[/LIST]
Since we don't know what you are actually trying to achieve with your code, it's hard to tell which is better. Note that however the first way is not recommended since its functionality relies on the order of performing the static assignments (which is surely define somewhere but only few Java developers would really know).

So, you got Solution No.1:
[PHP]
import java.util.Scanner;
import java.util.GregorianCalendar;
import javax.swing.*;

class Bank{
    
    static private double bal;   //Account balance
    static int withdraw;      //amount of times withdrawn
    
    static void setBal(double amount){bal = amount;}
    static double getBal(){return bal;}
    
    public static void main(String[] args){
        //code
    }
}

class Charge extends Bank{
    
    static double fee = Bank.withdraw * 0.10;
    static double tempbal = Bank.getBal();
    static double amount = tempbal - fee ;
    static {
        Bank.setBal(amount);
    }
}[/PHP]

...and Solution No. 2:
[PHP]
import java.util.Scanner;
import java.util.GregorianCalendar;
import javax.swing.*;

class Bank{
    
    static private double bal;   //Account balance
    static int withdraw;      //amount of times withdrawn
    
    static void setBal(double amount){bal = amount;}
    static double getBal(){return bal;}
    
    public static void main(String[] args){
        //code
    }
}

class Charge extends Bank{
    
    double fee = Bank.withdraw * 0.10;
    double tempbal = Bank.getBal();
    double amount = tempbal - fee ;
    public Charge() {
        Bank.setBal(amount);
    }
}[/PHP]

Hope that helps.

---

