---
title: "Problem with Java"
date: 2009-03-25
forum: Programming Talk
---

### Post by joshuapbell on 2009-03-25
Okay so I am trying to write a very simple java program, basically it adds two numbers (inputed by the user) and then displays the results. Here is the issue every time I run it it freezes, and I am unable to do anything with it.  

I am using eclipse..

As far as I can tell everything is good with the code... So I am not sure what is going on unless I am just over looking something. Any help would be appreciated thanks.

```

//Addition program that displays the sum of two numbers.

//Java Packages
import javax.swing.*;

public class Addition {
	// main method begins with execution of Java Application
	public static void main(String args[]) 
	{
		
		String firstNumber;		// first string entered by user
		String secondNumber;	// second string entered by user
		
		int number1;			// first number to add
		int number2;			// second number to add
		int sum;				// sum of number1 and number2
		
		// read in first number from user as String
		firstNumber = JOptionPane.showInputDialog ("Enter first integer" );
		secondNumber = JOptionPane.showInputDialog ("Enter second integer" );
		
		// convert numbers from type String to type int
		number1 = Integer.parseInt( firstNumber );
		number2 = Integer.parseInt( secondNumber );
		
		// add numbers
		sum = number1 + number2;
		
		// display results
		JOptionPane.showMessageDialog(null, "The Sum is " + sum, "Results", JOptionPane.PLAIN_MESSAGE );
		
		System.exit( 0 ); // terminate application with window
		
	} // end method main

} // end class Addition



```

---

### Post by dwhitney67 on 2009-03-25
The application works fine on my system.  I have the 'openjdk-6-jdk' package installed.

---

### Post by jespdj on 2009-03-25
I just tried running your code (on Windows) and it works fine.

What do you mean exactly with "it freezes"? What do you see? When exactly does it freeze?

Some older versions of Java have problems with Swing and Ubuntu's desktop effects, which can lead to Swing windows only showing a grey rectangle. Try disabling the desktop effects and running it again, if this is what you get.

---

### Post by joshuapbell on 2009-03-25
> **jespdj said:**
> I just tried running your code (on Windows) and it works fine.

What do you mean exactly with "it freezes"? What do you see? When exactly does it freeze?

Some older versions of Java have problems with Swing and Ubuntu's desktop effects, which can lead to Swing windows only showing a grey rectangle. Try disabling the desktop effects and running it again, if this is what you get.

I have the same package as the previous poser mentions

when I run it it opens the first dialog, asking for the first integer, then does not allow me to enter the integer, or press any buttons. and I have to stop it to get rid of the windows. I have tried enabling, and disabling compiz to no avail

---

### Post by sujoy on 2009-03-25
well the code runs fine here too

jdk 6u12-1, jre 6u12-1 in arch

---

### Post by theDaveTheRave on 2009-03-25
joshuapbell

Are you running the app from the cli or from within eclipse??

Personally I use netbeans (but that is personal choice, that may soon change!), and I know that sometimes if I run a program that I have compiled with it, and run previously it will suddenly hang the system on me?

I would ask you to post your system details, but I have this issue on running a very small application that only copies and re-names a file, and I'm running it on a fairly well spec'd 64bit desktop (oddly enough my much poorer spec 32bit laptop doesn't have this issue).


I still haven't been able to work out why, but if I run the program from the cli I don't get this problem, or at least when I do I am able to "break away" and stop the problems, rather than needing to perform a hard reset.

I don't know if this helps.

Alternatively you could then test to see if grabbing the details from the cli  will also cause problems?

David

---

### Post by joshuapbell on 2009-03-25
> **theDaveTheRave said:**
> joshuapbell

Are you running the app from the cli or from within eclipse??

Personally I use netbeans (but that is personal choice, that may soon change!), and I know that sometimes if I run a program that I have compiled with it, and run previously it will suddenly hang the system on me?

I would ask you to post your system details, but I have this issue on running a very small application that only copies and re-names a file, and I'm running it on a fairly well spec'd 64bit desktop (oddly enough my much poorer spec 32bit laptop doesn't have this issue).


I still haven't been able to work out why, but if I run the program from the cli I don't get this problem, or at least when I do I am able to "break away" and stop the problems, rather than needing to perform a hard reset.

I don't know if this helps.

Alternatively you could then test to see if grabbing the details from the cli  will also cause problems?

David

When I run things through the CLI, everything works fine.. so maybe it is just a bug with eclipse...

---

### Post by Shin_Gouki2501 on 2009-03-25
check your eclipse settings for compiler and runtime. :)

---

### Post by joshuapbell on 2009-03-25
> **Shin_Gouki2501 said:**
> check your eclipse settings for compiler and runtime. :)

what do you mean by this, how and what am I looking for?

---

### Post by Shin_Gouki2501 on 2009-03-25
right click your project -> buildpath -> configure buildpath
there you got: java compiler
and under java buildpath jre system library.

---

### Post by joshuapbell on 2009-03-25
then what?

---

### Post by Shin_Gouki2501 on 2009-03-25
post what stands there for compiler and jre, just in case.

---

### Post by joshuapbell on 2009-03-25
> **Shin_Gouki2501 said:**
> post what stands there for compiler and jre, just in case.

I am sorry, I just don't understand what you are asking for... am I just that stupid... that I will never be able to figure this out??

Or is there something I am missing...

---

