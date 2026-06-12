---
title: "Java crazy looping without input."
date: 2008-11-18
forum: Programming Talk
---

### Post by pcjunkie on 2008-11-18
What I am getting is this...

> please enter your hours 
InValid input, please try again!
please enter your hours 
InValid input, please try again!
please enter your hours 
InValid input, please try again!
please enter your hours 
InValid input, please try again!
please enter your hours 
InValid input, please try again!


From this

```

boolean inValid = false;

while (!inValid) //true
	{
	try {  
	loop1: do {				
			System.out.println("please enter your hours "); // Print the variable
			if (sc.hasNextInt()) {	 
			 userid= sc.nextInt();  
			} else {  
				inValid = !true; // attempt to prevent it skipping the entire program.    
				System.out.println("InValid input, please try again!");    
				} 
			}   
		while  (!inValid);
			
		System.out.println("Calculating payment");	
	          }
	catch (Exception e) 
		{ 
			System.out.println("I caught a cold, pass me the Benadryl please.."); continue;
		}	
			
```

I don't understand how it can bypass the input, assume its false input and continue looping forever each time receiving no input? Even if I force the loop, there is code asking a question that's not been answered. 
Its asking for the input, then skipping that part of the code? 
How can it do that?
Am I missing a brain, a latte, a career change?

---

### Post by Reiger on 2008-11-18
And what happens should the sc.hasNextInt() return false...? ;)

---

### Post by pcjunkie on 2008-11-18
it skips the entire sequence. nothing is added to 5 fields further down.

Still working on the thing but the basic concept is this...

For each field requiring a number I hope to bullet proof it as best I can with what little I know. 

If an entry fails it should repeat, later on only 2 times. for now I can't get the do while to repeat without it going stupid..

Even if I remove the rest of the code a repeating loop skips the input field and the if()....it shouldn't. How can add up to 10 or something if it skips the reason it repeats?

//overtime is basic, need to include first 38 hrs + extra as overtime
```
import java.util.Scanner;
  
public class View{
	 
	public static void main(String args[] ) throws Exception  {
 
	String firstname = null; 
	String lastname = null; 
	String fullname = null;
	int payid =1; 
	int test = 0; 
	int userid =0;
	double payrate=0;
	double hours =0;
	double grosspay =0;
	double netpay =0;
	double taxrate = 0.42;
	double taxpaid =0;
	boolean Valid = false;
	 
	Scanner sc = new Scanner(System.in);   
	 	
			System.out.println("please enter your Firstname "); // Print the variable
			if (sc.hasNext()) {
			firstname = sc.next(); 
			 
			}else {  System.out.println("InValid input, please try again!");
					firstname = sc.next(); 
				} 
			 	
			System.out.println("please enter your Lastname "); // Print the variable
			if (sc.hasNext()) {
			lastname = sc.next(); 
			} else {    
				System.out.println("InValid input, please try again!");
				Valid = true;
				}   
				fullname = firstname + " " + lastname; 	
	
	while (!Valid) 
	{ 		
			System.out.println("please enter your Payid "); // Print the variable
			if (sc.hasNextInt()) {
			payid = sc.nextInt(); 
			} else {  
				Valid = !true;     
				System.out.println("InValid input, please try again!");    
				} 
	  }	 
	 if ((payid <4) || (payid >1)) {
		switch(payid){
            case 1:
                //Executed if the value of Payid is 1.
                payrate = 55.00;
                Valid = true;
                break;
            case 2:
                //Executed if the value of Payid is 2.
                payrate = 33.00;
                Valid = true;
                break;
            case 3:
                //Executed if the value of Payid is 3.
                payrate= 25.00;
                Valid = true;
                break;
            case 4:
                 //Executed if the value of Payid is 4.
               payrate= 20.00;
                Valid = true;
                break;
            default:
		/* Loop reurns to loop if there is an error which there should not be */
                 System.out.println("InValid input, please try again!");
                break; 
			} 
		}
 
	// Name classes in order of exicution or exceptions will occur! 
	 EmployeePayroll EP = new EmployeePayroll( firstname, lastname, fullname, userid, payid, hours, payrate, grosspay, netpay, taxrate, taxpaid );
	 EP.showEmployeePayroll();	 
		  
	}
}

```

```


/*----------------------------------------------------------------------------------------------------------//
Employee Payroll Class
Function To calculate wages of an employee
w tax overtime and remainders
Author: ha ha funny ha ha
 
Calculate gross and net wages using Java with a focus on classes
 
----------------------------------------------------------------------------------------------------------*/

import java.util.Scanner;
import java.text.DecimalFormat;

public class EmployeePayroll{

	private String firstname, lastname, fullname;
	private int userid, payid;
	private double hours, payrate, grosspay, netpay, taxrate, taxpaid;
	DecimalFormat dec = new DecimalFormat("$0.00");  
	 
	
	public EmployeePayroll(){
		fullname = null;
		lastname=null;
		firstname=null;
		userid= 0 ;
		hours= 0;
		grosspay= 0;
		netpay = 0; 
		taxrate = 0;
		payrate= 0; 		
		payid = 0;
		taxpaid = 0;
		
	}
		public EmployeePayroll(String firstname, String lastname, String fullname) {
		this.firstname = firstname;
		this.lastname = lastname;
		this.fullname = fullname;
 
	}
	public EmployeePayroll(String firstname, String lastname, String fullname, int userid, int payid ){
		this.firstname = firstname;
		this.lastname = lastname;
		this.fullname = fullname;
		this.userid = userid;
		this.payid = payid;
	
	
	
	}
	public EmployeePayroll(String firstname, String lastname, String fullname, int userid, int payid, double hours, double payrate, double grosspay, double netpay, double taxrate, double taxpaid) { 
		this.firstname = firstname;
		this.lastname = lastname;
		this.fullname = fullname;
		this.userid = userid;
		this.payid = payid;
		this.hours = hours;
		this.payrate = payrate;
		this.grosspay = grosspay;
		this.netpay = netpay;
		this.taxrate = taxrate;
		this.taxpaid = taxpaid;
	}
	 
	public void setFirstname(String firstname){
		this.firstname = firstname;
	}
	
	public void setLastname(String lastname){
		this.lastname = lastname;
	}
	public void setUserid(int userid){
		this.userid = userid;
	}
	 public void setFullname(String  fullname){
		
		 this.fullname = fullname;	 
	}
	
	public void setPayid(int payid){
		
		this.payid = payid;
	}
   	public void setHours(double hours){ 
 
		this.hours = hours;
  
	}	
	public void setPayrate(double payrate){	
		
		this.payrate = payrate;
	}
	public void setGrosspay(double grosspay){	
		
		this.grosspay = grosspay;
	}
	public void setNetpay(double netpay){	
		
		this.netpay = netpay;
	}
	public void setTaxrate(double taxrate){	
		
		this.taxrate = taxrate;
	}
	public void setTaxpaid(double taxpaid){	
		
		this.taxpaid = taxpaid;
	}
	public String getLastname(){
		
		return this.lastname;		
	}
	public String getFirstname(){
		
		return this.firstname;		
	}
	 public String getFullname(){
		
		return this.fullname;
	}
	public int getUserid(){
		
		return this.userid;
	}
	public int getPayid(){
		
		return this.payid;
	}
	public double getHours(){
		
		return this.hours;
	}
	
	public double getPayrate(){
		
		return this.payrate;
	}
	 
	public double getGrosspay( ){
		
		if (hours < 38 ) {
			
			grosspay = hours * payrate;
		}
		
		if (hours > 42) {
			
			grosspay = hours * payrate ;
		}
	 
		return this.grosspay;
	}
	
	public double getTaxrate(){
		
		return this.taxrate;
	} 
	
	public double getTaxpaid( ){
			
			taxpaid = grosspay * taxrate;
		
		return this.taxpaid;
	}
	public double getNetpay( ){
			/* hack required*/
			double tax = 0;
			tax = grosspay * taxrate;
			netpay = grosspay - tax;
		
		return this.netpay;
	}
	 
	public void showEmployeePayroll(){
		System.out.println(" FullName: " +this.getFirstname());
		System.out.println(" LastName: " +this.getLastname());
		System.out.println(" Employee: " +this.getFullname());
		System.out.println(" UID: "          +this.getUserid());
		System.out.println("Total hours: " +this.getHours());
		System.out.println("Pay ID: " + dec.format( this.getPayid()));
		System.out.println("Payrate: " +dec.format(this.getPayrate()));
		System.out.println("Grosspay: " +dec.format (this.getGrosspay()));
		System.out.println("Taxrate;  " +this.taxrate);
		System.out.println("Netpay: " +dec.format( this.getNetpay()));
		System.out.println("Taxpaid: " +dec.format( this.getTaxpaid()));
		System.out.println("Taxpaid: " +dec.format( this.getTaxpaid()));
		System.out.println("Taxpaid: " +dec.format( this.getTaxpaid()));
		/* Date now = new Date();
		long nowLong = now.getTime(); */
		
		
	}
	 
}


```

---

### Post by PaulM1985 on 2008-11-19
Does Java allow hasNext() when Scanner is using the keyboard as an input type?

I am not sure if it is allowed, because I would have thought the computer would know if you where intending on typing anything.

It may be worth changing the if statements within your do-while loops so that you do a test to see if the String/int or whatever is valid, and if not it asks again, without using the hasNext() method.

So for example:

int age;

Scanner sc = new Scanner(System.in);

System.out.println("Welcome to club 18-30.");
System.out.println("Please enter your age, Only between 18 and 30.")

age = sc.nextInt();

while(age<18 || age>30)
{
System.out.println("I think you got your age wrong, between 18 and 30 please");
age = sc.nextInt();
}


I hope this helps a little

Paul

---

### Post by PandaGoat on 2008-11-19
In the else of if(keyboard.hasNextInt()) you need to remove the input that was not an integer from the stream.  If you don't, hasNextInt() will continue to return false based on the first inpu--without blocking for more input.

So something like this:
[php]
if (sc.hasNextInt()) {	 
  userid= sc.nextInt();  
} else {  
  inValid = !true; // attempt to prevent it skipping the entire program.    
  System.out.println("InValid input, please try again!");    
  keyboard.Next(); // remove the non-int from the stream
} 
[/php]

---

### Post by drubin on 2008-11-19
> **PandaGoat said:**
> 
[php]
...
  inValid = !true; // attempt to prevent it skipping the entire 
....
} 
[/php]

Is there a reason why you chose the above?

This would not have been easier to read/follow?
[PHP]
inValid = false;
[/PHP]

---

