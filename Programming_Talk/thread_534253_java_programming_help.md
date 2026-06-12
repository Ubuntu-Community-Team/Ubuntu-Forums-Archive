---
title: "java programming help"
date: 2007-08-25
forum: Programming Talk
---

### Post by Nolander on 2007-08-25
hi all,

im writing a java class that i have 2 do 4 n assesment at skool but im stuck a 1 point so if any one can help that would be gr8.

```

import javax.swing.JOptionPane;

public class Pay

{
    public static void main (String[] args)
    {		
	String hoursWorked_string, paySelect_string;
	int paySelect, payRate;
	double hoursWorked, grossPay;

	hoursWorked_string = JOptionPane.showInputDialog("How manyhours did you work:");
	hoursWorked = Integer.parseInt(hoursWorked_string);
		
	paySelect_string = JOptionPane.showInputDialog("What is your pay rate \n 1 $17.00 \n 2 $20.00 \n 3 $22.00");
	paySelect = Integer.parseInt(paySelect_string);

	switch(paySelect)
	{
	case 1:
		payRate = 17;
		break;
	case 2:
		payRate = 20;
		break;
	case 3:
		payRate = 22;
		break;
	}

	grossPay = hoursWorked * payRate;

	JOptionPane.showMessageDialog(null,"Your gross pay is"+grossPay);//shows results
	System.exit(0);
    }
}
```

when i compile the above i get:
```
Pay.java:37: variable payRate might not have been initialized
        grossPay = hoursWorked * payRate;
                                 ^
1 error


```

ta,
Nolander.

---

### Post by jtuchscherer on 2007-08-25
In your code it is a possibility that the pay rate is null which would lead to an error in the multiplication.
if you initialize the pay rate like this:

int payRate = 0;

your code will compile .

HTH
johannes

---

### Post by jordanmthomas on 2007-08-25
add this line before your switch statement:
```
payRate = -1;
```

and just check later on to make sure it's not -1 (meaning one of your switches was executed)

The problem is that after your switch statements payRate may still point to nothing.  What if paySelect is not 1, 2, or 3?  In this case payRate is nothing.  Even if you know that paySelect will be 1, 2, or 3, the compiler doesn't so it gives an error.

You may also be able to add a default case to your switch statement, but I am not sure if it will still generate errors or not (you can always try, right?)

---

### Post by Nolander on 2007-08-25
thanks that did it. :)

---

### Post by ekravche on 2007-08-25
never mind... :)

---

