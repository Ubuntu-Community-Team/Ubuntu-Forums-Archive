---
title: "Write your own exception in java !!!"
date: 2012-11-05
forum: Programming Talk
---

### Post by vikkyhacks on 2012-11-05
>  /* filename : myException.java
public class myException extends Throwable{ 
	private static final long serialVersionUID = 1L;	
	public String getMessage(){
		return "that was not good";
	}
}

> 
/* filename : myMain.java */
import java.util.Scanner;
public class myMain {	
	public static void main(String[] args) {		
		Scanner s = new Scanner(System.in);		
		try {
			int n1 = s.nextInt();
			int n2 = s.nextInt();
			System.out.print(n1/n2);
		} catch(myException a) {
			System.out.print(a.getMessage());
		}
	}
}


When I run this code I get the error message
> pack/myMain.java:14: error: exception myException is never thrown in body of corresponding try statement
		} catch(myException a) {
		  ^

MY QUESTIONS :
1. I cant understand what this error means ?
2. I need the program to throw the error message "that was not good" when n2 turns out to be zero, Is that possible ?

.... just a beginner with java, sorry if I am too noobish  :)

---

### Post by dwhitney67 on 2012-11-05
> **vikkyhacks said:**
> When I run this code I get the error message


MY QUESTIONS :
1. I cant understand what this error means ?
2. I need the program to throw the error message "that was not good" when n2 turns out to be zero, Is that possible ?

.... just a beginner with java, sorry if I am too noobish  :)

Answers...

1.  The nextInt() methods throws one of these possible exception types:  InputMismatchException, NoSuchElementException , or IllegalStateException.  It does not throw myException nor any other type of exception that you may want it to.

2.  When calling nextInt(), the number 0 is valid input.  If you want to throw an exception for such a case, then I would suggest that you implement your own "Scanner" class that encapsulates the behavior of Scanner.  For example:
```

import java.util.Scanner;
import java.util.InputMismatchException;
import java.util.NoSuchElementException;
import java.lang.IllegalStateException;

class MyScanner
{
    private String ErrorMessage = "Input is not valid.";
    private Scanner s;

    public MyScanner()
    {
        s = new Scanner(System.in);
    }

    public int nextInt() throws InputMismatchException,
                                NoSuchElementException,
                                IllegalStateException
    {
        int n = 0;
        try
        {
            n = s.nextInt();    // let Scanner get the input

            if (n == 0)         // here we check if number is 0
            {
                throw new InputMismatchException(ErrorMessage);
            }
        }
        catch (InputMismatchException e)
        {
            throw new InputMismatchException(ErrorMessage);
        }
        return n;
    }
}

public class myMain
{
    public static void main(String[] args)
    {
        MyScanner s = new MyScanner();
        try
        {
            System.out.print("Enter a number: ");
            int n1 = s.nextInt();
            System.out.print("Enter another number: ");
            int n2 = s.nextInt();
        }
        catch (InputMismatchException e)
        {
            System.err.println(e.getMessage());
        }
    }
}

```

---

### Post by vikkyhacks on 2012-11-05
> **dwhitney67 said:**
> 
1. The nextInt() methods throws one of these possible exception types: InputMismatchException, NoSuchElementException , or IllegalStateException. It does not throw myException nor any other type of exception that you may want it to.

... thanks, It helped me reprogram (sorry I din use caps for class names) ...

**I DO HAVE A QUESTION (in the end) **


So its like this now ...
```

/* file name - myMain.java */
public class myMain {
	
	public static void main(String[] args) {
		myScanner SS = new myScanner();
		try {
			int n1 = SS.nextInt();
			int n2 = SS.nextInt();
			System.out.println(n1/n2);
		} catch(myException m) {
			System.out.print(m.getMessage());
		}
	}
}

/* file name : myScanner.java */
import java.util.*;
public class myScanner{	
	private int num=0;
	private Scanner myS;	
	public myScanner() {
		myS = new Scanner(System.in);
	}	
	public int nextInt() throws myException {
		num = myS.nextInt();
		if(num == 0) {
			throw new myException();
		}
		return num;		
	}
}

/* file name : myException.java */
public class myException extends Exception {
	private static final long serialVersionUID = 1L;	
	public String getMessage() {
		return "Invalid input !!!!";
	}
}

```

[B]the exception is thrown if 0 is the input, I have modified the scanner class for it but
is it possible to throw the exception while the division is performed ?
like I need the exception to be thrown at the line[/B]
> System.out.println(n1/n2)

---

### Post by vikkyhacks on 2012-11-06
and just asking out of box, The way you format your code is like
```

function_name 
{
    if(blab blab ...)
    {
    }
    else
    {
    }
}

while mine looks like 

function_name {

    if(blab blab ...) {

    } else {

    }
}

```

do we have any names for this kind of formatting ??? like there is [camelcase]("http://en.wikipedia.org/wiki/CamelCase") kinda stuff for naming variables, I don know how to google for this question, If someone is closing this thread for this question, please close after telling how i can google this

---

### Post by r-senior on 2012-11-06
Code layout is a personal or project preference. Your layout is very similar to what Sun/Oracle recommend and is what I would prefer if I was editing your code.

[http://www.oracle.com/technetwork/java/javase/documentation/codeconvtoc-136057.html](http://www.oracle.com/technetwork/java/javase/documentation/codeconvtoc-136057.html)

In particular:

[http://www.oracle.com/technetwork/java/javase/documentation/codeconventions-142311.html#431](http://www.oracle.com/technetwork/java/javase/documentation/codeconventions-142311.html#431)

You can mark the thread solved. There should be an option near the top of the page.

---

### Post by vikkyhacks on 2012-11-06
> **r-senior said:**
> You can mark the thread solved. There should be an option near the top of the page.

I am not done yet ...

the exception is thrown if 0 is the input, I have modified the scanner class for it but
is it possible to throw the exception while the division is performed ?
like I need the exception to be thrown at the line

***_System.out.println(n1/n2)_***

---

### Post by dwhitney67 on 2012-11-06
> **vikkyhacks said:**
> I am not done yet ...

the exception is thrown if 0 is the input, I have modified the scanner class for it but
is it possible to throw the exception while the division is performed ?
like I need the exception to be thrown at the line

***_System.out.println(n1/n2)_***

Inherently the answer is no.  If you want your print statements to perform a specific/custom action, then you will need to implement this yourself.  In other words, create a wrapper class that serves to perform arithmetic checks on the data before it is printed.

---

### Post by r-senior on 2012-11-06
> **vikkyhacks said:**
> I am not done yet ...
I meant that you can close it yourself when you want to, not that you should close it now. ;)

---

### Post by vikkyhacks on 2012-11-06
> **dwhitney67 said:**
> Inherently the answer is no.  If you want your print statements to perform a specific/custom action, then you will need to implement this yourself.  In other words, create a wrapper class that serves to perform arithmetic checks on the data before it is printed.


thanks for the reply, but I don wish to change the print function
I want the operator to throw the exception
```
public class myMain {	
		public static void main(String[] args) {
			int n=0;
                        n = 12/0;
			System.out.println(n);
	}
}
```
the following code throws the exception as
```

Exception in thread "main" java.lang.ArithmeticException: / by zero
	at pack.myMain.main(myMain.java:7)
```

In C++ we have operator overloading to change the operator's behavior at runtime, any such modifications or ideas such that the "/" throws myException (the exception that I wrote) in these case ??? If it can throw an arithmetic exception then there should be a way to throw user defined exceptions .... :)

---

### Post by kevinharper on 2012-11-06
I think dwhitney67's solution is perfect: check data to make sure it's valid before using/displaying it.

What's the advantage of having it work the way you are wanting it to work?

PS: Trust me, dwhitney67 knows what he's talking about in all-things-programming.

---

### Post by spjackson on 2012-11-07
> **vikkyhacks said:**
> 
In C++ we have operator overloading to change the operator's behavior at runtime, any such modifications or ideas such that the "/" throws myException (the exception that I wrote) in these case ??? If it can throw an arithmetic exception then there should be a way to throw user defined exceptions .... :)
Java does not have operator overloading. You cannot change the behaviour of /

Options:
1. 
```

if (n2 == 0) {
    throw new MyException();
}
System.out.println(MyArithmetic.integerDivide(n1, n2));

```

2.
```

try {
    System.out.println(n1 / n2);
}
catch (java.lang.ArithmeticException arithmeticException) {
    throw new MyException();
}

```

3. Replace the operator with some class & function which avoids or translates the arithmeticException as above.
```

System.out.println(MyArithmetic.integerDivide(n1, n2));

```

---

### Post by dwhitney67 on 2012-11-07
> **kevinharper said:**
>  
PS: Trust me, dwhitney67 knows what he's talking about in all-things-programming.
Thanks for the commendation, however I can assure you that I don't know everything related to programming.  I experiment a lot, try to read, and I try to remember what works and what doesn't.

As spjackson has pointed out to the OP, operator-overloading is a feature that is not available with Java.  Oftentimes if one wants specialized behavior from their application that is not provided by the constructs of the language itself, then one must develop a wrapper function/class to provide the functionality they desire.

---

