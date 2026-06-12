---
title: "Java - Printing only one of the numbers from a certain inputed multi-character number"
date: 2009-09-02
forum: Programming Talk
---

### Post by s3a on 2009-09-02
My teacher gave me homework and part of it is this which is basically an attempt in printing only one of the series of numbers. For example, to print 9 or 8 or 7 etc out of 123456789. (At least that's how I understood it)The following is my code:

[I]//INCOMPLETE!!!!!!!!!!!! ANALYZE THIS FURTHER!!!!!

import java.util.Scanner;

public class One

{

	public static void main (String [] args)
	
	{
	
	Scanner kb;
	
	kb = new Scanner (System.in);
	
	System.out.print("Enter any number: ");
	
	double number = (int) kb.nextDouble();
	
	//1s place WTF?!
	System.out.println(number % 1);
	
	//10s place
	System.out.println(number % 10);
	
	//100s place
	System.out.println(number % 100);
	
	}
}[/I]

Here is the question just in case I misunderstood it:

You are not required to write programs for Questions 1-8. You could, of course, write programs to
verify your answers; if you so decide, make sure you answer the questions before getting help from
the JVM.
   1. Suppose you have a variable called number.
       (a) Write a Java expression to produce the last (i.e., the 1s place) digit of the number.
       (b) Write a Java expression to produce the second-to-last (i.e., the 10s place) digit of the
           number.
       (c) Write a Java expression to produce the third-to-last (i.e., the 100s place) digit of the
           number.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by Finalfantasykid on 2009-09-02
Personally what I would do, is create a new string, which is the number provided. 

then there is a method in the Java documentation which should be very handy for this ;)
[U]
[http://java.sun.com/javase/6/docs/api/java/lang/String.html](http://java.sun.com/javase/6/docs/api/java/lang/String.html)
[/U]

---

### Post by pbrockway2 on 2009-09-03
I agree with regarding this as a String question, but if you are going to use the % operator then remember what it means: remainder after division by whatever.

So n%1 is zero ("n divided by 1 is n *remainder 0*")

To get the 1's digit you would look at the remainder when you divide by 10...

---

### Post by Finalfantasykid on 2009-09-03
There is another problem with using modulus, and that is if for example you do number % 100, you will get a 2 digit number probably, and from what I understand, you are only supposed to get a 1 digit number.  So you would have to do more calculations to get it down to a single digit, like maybe divide by 10(then floor() ).  Which is over complicating what can be done if you were to use Strings instead.

---

### Post by pbrockway2 on 2009-09-03
Actually you don't need the floor() if you are using integer division.

---

### Post by Finalfantasykid on 2009-09-03
I would have probably used doubles or floats, since with ints, I don't think it will always round down, sometimes it will round up (right?).  In this case, it has to always round down to be correct.

---

### Post by Reiger on 2009-09-03
> **Finalfantasykid said:**
> I would have probably used doubles or floats, since with ints, I don't think it will always round down, sometimes it will round up (right?).  In this case, it has to always round down to be correct.
Negative values, yes.

---

### Post by NovaAesa on 2009-09-03
Sometimes a rounddown is performed (if the result of the division is a positive number) or a roundup is performed (if the result is a negative number). The better way to think about it is that the part of the result after the decimal place is truncated leaving a simple integer.

---

### Post by s3a on 2009-09-04
I solved this by doing / by 1 followed by a specific number of zeroes then % 10 if I recall correctly.

---

