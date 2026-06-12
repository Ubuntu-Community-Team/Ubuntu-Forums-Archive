---
title: "[Java] method not recognized"
date: 2009-02-17
forum: Programming Talk
---

### Post by gotenks05 on 2009-02-17
I'm working on a Java program as an assignment for my programming class.  I'm supposed to have two Java classes, one that contains the methods and one that demonstrates the class that has the methods.  It is supposed to be something like payroll.  When I compile it, everything seems alright with the main class, but I'm getting problems with the other class file, which won't let me compile the program completely.

My terminal says:

> ./Payroll.java:46: missing method body, or declare abstract 
        public double getGross(); 
                      ^ 
./Payroll.java:48: return outside method 
                return PayRate * hours; 
                ^ 
2 errors 


the code for the first class is this:

```
public class Payroll
{
	String name;
	double ID, PayRate, hours;

	public void setName(String nam)
	{
		name = nam;
	}

	public String getName()
	{
		return name;
	}

	public void setID(double  ver)
	{
		ID = ver;
	}

	public double getID()
	{
		return ID;
	}

	public void setPayRate(double pay)
	{
		PayRate = pay;
	}

	public double getPayRate()
	{
		return PayRate;
	}

	public void setHours(double hour)
	{
		hours = hour;
	}

	public double getHours()
	{
		return hours;
	}

	public double getGross();
	{
		return PayRate * hours;
	}
}
```

the code for the main class is this:

```
import java.util.*;
public class PayrollDemo
{
	public static void main(String[] args)
	{
		String name;
		double ID, pay, hours;
		Scanner keyboard = new Scanner(System.in);

		System.out.print("Enter your name: ");
		name = keyboard.nextLine();

		keyboard.nextLine();

		System.out.print("Enter your ID number:  ");
		ID = keyboard.nextDouble();

		System.out.print("Enter your hourly pay rate:  ");
		pay = keyboard.nextDouble();

		System.out.print("Enter the hours worked:  ");
		hours = keyboard.nextDouble();

		Payroll payroll = new Payroll();

		payroll.setName(name);
		payroll.setID(ID);
		payroll.setPayRate(pay);
		payroll.setHours(hours);

		System.out.println("ID:  " + payroll.getID());
		System.out.println("Name:  " + payroll.getName());
		System.out.println("Hourly pay:  " + payroll.getPayRate());
		System.out.println("Hours worked:  " + payroll.getHours());
		System.out.println("Gross pay:  " + payroll.getGross());
	}
}
```

What am I doing wrong in the Payroll class to get this error?

---

### Post by simeon87 on 2009-02-17
You have a semi-colon at the end:

```

public double getGross();

```

So Java thinks it's an empty method. This is also why the return statement appears to be outside the method.

---

### Post by gotenks05 on 2009-02-17
> **simeon87 said:**
> You have a semi-colon at the end:

```

public double getGross();

```

So Java thinks it's an empty method. This is also why the return statement appears to be outside the method.


Thanks.

---

