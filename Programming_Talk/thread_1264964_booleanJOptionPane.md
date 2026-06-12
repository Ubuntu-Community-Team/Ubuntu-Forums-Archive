---
title: "boolean/JOptionPane"
date: 2009-09-12
forum: Programming Talk
---

### Post by s3a on 2009-09-12
What is wrong with my code?:

```
import javax.swing.JOptionPane;

public class Boolean

{
	public static void main (String [] args)
		{
			
		String value;
		value = JOptionPane.showInputDialog("Enter a value for x.");
			
			boolean x = 2;
			
			if(x = true)
				JOptionPane.showMessageDialog(null, "x is equal to 2");
			else
				JOptionPane.showMessageDialog(null, "x is not equal to 2");
				
		}
}
```

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by myrtle1908 on 2009-09-12
> **s3a said:**
> What is wrong with my code?

Plenty.

1. Don't name your class 'Boolean'.  There is already a core Java class named 'Boolean' which wraps the primitive Java type *boolean*.  If you absolutely must have a name clash then at least place your class in a package.  This is not the main problem with your code however and will not in most cases prevent you from a successful compile.

2. Your code doesn't compile.  Why?  Have you read the error when you attempt to compile?

```
Boolean.java:6: incompatible types
found   : int
required: boolean
                boolean x = 2;
```

Have a think about what the means.  You are attempting to set an int (the number 2) to a boolean type.  This will never work.

3.  Why are you prompting for 'x' yet never using the value that user inputs?

4.  if (x = true) ... you are not testing for equality here.  A single equals sign is for assignment.

You really seem to lack a basic understanding of programming concepts.  I believe several other members have pointed this out previously.  I appreciate that you are learning but you have to give (read try) a little before you get something back.

---

### Post by s3a on 2009-09-13
I changed the code a bit from before but if boolean can have only true or false values then how come my teacher's following code works?:

```
boolean isLeapYear = (year % 400 == 0) && (year % 100 != 0) || (year % 4 == 0);
```

By the way I dropped the JOptionPane thing until I understand the boolean concept since my teacher did not teach or even mention JOptionPane. I just wanted to make popup windows which I've done succesfully in super simplistic programs before but that's it. It's more important that I understand the boolean concept so that I can start reading on the switch statement.

---

### Post by falconindy on 2009-09-13
Because your teacher's code is comparing two values to return true or false. The result of the 3 comparisons is combined with and operators to return a single true or false result.

In extreme pseudo-code: If dividing the current year by 400 does not produce remainder AND dividing the current year by 100 does produce a remainder AND dividing the current year by 4 does not produce a remainder, then its a leap year.

---

### Post by s3a on 2009-09-13
Ok but for basic code so that I can really have a feel for how it works, how do I turn this mini-program:

```
import java.util.Scanner;

public class test

{
	public static void main (String [] args)
		{
			
		Scanner kb;
		kb = new Scanner(System.in);
		
		System.out.print("Enter an integer: ");
		
		//int value1 = (int)kb.nextInt();
		
		boolean value = true;
		
		if (value = true)
		System.out.println("2");
		
		if(value = false)
		System.out.println("not 2");
				
		}
}
```

into something that gives me the ability to get an input from the user and if it is the number 2 for it to print out "2" (true), and if it's not 2 to print out "not 2" (false). For some reason, I'm just not understanding how this boolean data type works.

---

### Post by falconindy on 2009-09-13
No, you're not understanding the difference between '=' and '==' as was posted earlier in this thread. The statement "if (value = true)" will **always **return true because its a variable assignment, not a comparison. The statement "if (value == true)" is an actual comparison.

---

### Post by s3a on 2009-09-13
Ok I see that now but:

```
import java.util.Scanner;

public class test

{
	public static void main (String [] args)
		{
			
		Scanner kb;
		kb = new Scanner(System.in);
		
		System.out.print("Enter an integer: ");
		
**		// Why doesn't the following line work? (when uncommented of course)**
		// int value = (int)kb.nextInt();
		
		
[B]		/* How can I make it so that the following statement assigns true or false
                   to a numerical value inputted by the user?
		   (if I replace "true" by a number, I get a compilation error. */[/B]
		   
		boolean value = true;
		
		if (value == true)
		System.out.println("2");
		
		if(value == false)
		System.out.println("not 2");
				
		}
}
```

---

### Post by falconindy on 2009-09-13
Really not sure what your goal here is... You can do the comparison of the user-input integer to a number and then assign true or false to a boolean variable. Then, output the value of the boolean.

```

int input = (int)kb.nextInt();
boolean value;
if (input == 2) { value = true; } else { value = false; }

System.out.println(value);

```
Value will be printed as 'true' or 'false'.

---

