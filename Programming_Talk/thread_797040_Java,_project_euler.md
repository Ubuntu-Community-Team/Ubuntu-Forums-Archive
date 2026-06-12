---
title: "Java, project euler"
date: 2008-05-16
forum: Programming Talk
---

### Post by DanielJackins on 2008-05-16
Hi, I'm currently trying to solve problem 25 on project euler, and I'm pretty sure I know how to solve the answer. Problem is, I am using Integer as a variable type, which can not handle the size of the numbers I need to use. I'm using Integer (not int) because a function I'm using to convert the number to a string isn't compatibile with int.
Anyone know how to overcome this? Here is my code.
[php]/*This program finds the sum of all the even numbers
in the Fibonacci sequence under four million*/



public class Fibonacci
{
	public static void main(String[] args) //All code goes in here
	{
		Integer num1=1;
		Integer num2=2;
		Integer num3=0;
		Integer num4=0;
		String check;
		
		while (num1 > 0)
		{
			num3 = num1 + num2;
			num4 = num3 + num2;
			num1 = num3 + num4;
			num2 = num4 + num1;
			
			check = num1.toString();
			if (check.length()>=1000)
			{
				System.out.println(num1);
			}

		}
	}
}[/php]

---

### Post by NormR2 on 2008-05-16
Would the class BigInteger work?

Are you getting an error with your current code?

What's the purpose of the following:
```
if (check.length()>=1000)
```

---

### Post by DanielJackins on 2008-05-17
Okay so I tried BigInteger, and here's my errors;

Fibonacci.java:10: incompatible types
found   : int
required: java.math.BigInteger
		BigInteger num1=1;
		                ^
Fibonacci.java:11: incompatible types
found   : int
required: java.math.BigInteger
		BigInteger num2=2;
		                ^
Fibonacci.java:12: incompatible types
found   : int
required: java.math.BigInteger
		BigInteger num3=0;
		                ^
Fibonacci.java:13: incompatible types
found   : int
required: java.math.BigInteger
		BigInteger num4=0;
		                ^
Fibonacci.java:16: operator > cannot be applied to java.math.BigInteger,int
		while (num1 > 0)
		            ^
5 errors


The if (check.length()>=1000) is to see if the integer has 1000 or over 1000 digits, which is what I'm trying to solve

---

### Post by Sportingfan on 2008-05-17
Integers and BigIntegers cannot be constructed like ints.

```
Integer i = new Integer(1);
```

This also yields for BigIntegers.
Look in the [api]("http://java.sun.com/javase/6/docs/api/") for BigInteger constructors.

---

### Post by NormR2 on 2008-05-17
As Sportingfan says, Integer and BigInteger are classes, not primitives like int. You have to use methods to manipulate their values.  Read the doc for those classes to see how to use them.

---

### Post by rye_ on 2008-05-17
Accidental double post, see below

---

### Post by rye_ on 2008-05-17
After seeing your post I tried this problem in ruby.  My code takes less than 0.05 seconds to return the answer, perl and python are known to run faster.  I'd be interested to know how long your solution takes to run.
if you're willing use at the command line;

time 'command to run the program'

this yields 3 time desciptions; real is the one of interest

An observation about your code; your test of the number of digits in a number relies on conversion to a string.  This will be a huge bottleneck.  it would be better to test each fibonacci series number against the first 1000 digit number. i.e.

test = 10^999 //first, smallest 1000 digit number //I'm not a java programmer so I'm ignoring type declarations
while (number < test){
  //increment number
}

best of luck,

ryan

---

### Post by DanielJackins on 2008-05-17
Whoops, double post, read down

---

### Post by DanielJackins on 2008-05-17
Okay, so I made some changes based on my best comprehension of you're suggestions (I am fairly new to Java and programming as a whole), and this is what I've come up with.
[php]
/*The Fibonacci sequence is defined by the recurrence relation:

    Fn = Fn&#8722;1 + Fn&#8722;2, where F1 = 1 and F2 = 1.

Hence the first 12 terms will be:

    F1 = 1
    F2 = 1
    F3 = 2
    F4 = 3
    F5 = 5
    F6 = 8
    F7 = 13
    F8 = 21
    F9 = 34
    F10 = 55
    F11 = 89
    F12 = 144

The 12th term, F12, is the first term to contain three digits.

What is the first term in the Fibonacci sequence to contain 1000 digits?
*/

import java.math.*;

public class Fibonacci
{
	public static void main(String[] args) //All code goes in here
	{
		BigInteger num1; 
		BigInteger num2;
		BigInteger num3;
		BigInteger num4;
		String check;
		Boolean test = false;
		
		num1.valueOf(1);
		num2.valueOf(2);
		num3.valueOf(0);
		num4.valueOf(0);
		
		while (test = false)
		{
			num3 = num1.add(num2);
			num4 = num3.add(num2);
			num1 = num3.add(num4);
			num2 = num4.add(num1);
			
			check = num1.toString();
			if (check.length()>=1000)
			{
				System.out.println(num1);
				test = true;
			}
		}
	}
}
[/php]

Which now returns errors saying variables num1-4 have not been declared :confused:, and yes I will time it once I get it running, Rye :)

---

### Post by NormR2 on 2008-05-17
I'd help a lot if you'd post here the FULL text of the error messages along with the command you used to get them.

> Which now returns errors saying variables num1-4 have not been declared

BTW
```
while (test = false) 
```
is an assignment statement, not a comparion (==)

if you want a forever loop just say

while (true)

---

### Post by DanielJackins on 2008-05-17
Right, sorry. Here are the error messages I get (when trying to compile);

Fibonacci.java:38: variable num1 might not have been initialized
		num1.valueOf(1);
		^
Fibonacci.java:39: variable num2 might not have been initialized
		num2.valueOf(2);
		^
Fibonacci.java:40: variable num3 might not have been initialized
		num3.valueOf(0);
		^
Fibonacci.java:41: variable num4 might not have been initialized
		num4.valueOf(0);
		^
4 errors

---

### Post by rye_ on 2008-05-17
Again I'm no java programmer, but I've hacked together some code to achieve a working solution;

```


import java.math.*;

public class Fibonacci
{
    public static void main(String[] args) //All code goes in here
    {
        BigInteger num1 = new BigInteger("0"); 
        BigInteger num2 = new BigInteger("0");
        BigInteger temp = new BigInteger("0");  
        BigInteger other = new BigInteger("0");
        BigInteger test = new BigInteger("10");
        
        
        int terms = 2; //stores the number of terms in the series considered
        num1 = num1.valueOf(1);
        num2 = num2.valueOf(1);
        other = other.valueOf(10);
     
        
        for (int count = 0; count < 998; count+=1){
        	test = test.multiply(other);
        } 
                 
        while (num2.compareTo(test) == -1){ //test fails
         
        	  temp = num1;
            num1 = num2;
            num2 = num2.add(temp);
            
	    terms = terms+=1;
        }
        System.out.println(terms);
    }
}  


```

funnily enough, the code above is about half as fast as my ruby script, 

Ryan

---

### Post by DanielJackins on 2008-05-17
[php]/*The Fibonacci sequence is defined by the recurrence relation:

    Fn = Fn&#8722;1 + Fn&#8722;2, where F1 = 1 and F2 = 1.

Hence the first 12 terms will be:

    F1 = 1
    F2 = 1
    F3 = 2
    F4 = 3
    F5 = 5
    F6 = 8
    F7 = 13
    F8 = 21
    F9 = 34
    F10 = 55
    F11 = 89
    F12 = 144

The 12th term, F12, is the first term to contain three digits.

What is the first term in the Fibonacci sequence to contain 1000 digits?
*/

import java.math.*;

public class Fibonacci
{
	public static void main(String[] args) //All code goes in here
	{
		BigInteger num1 = new BigInteger ("1");
		BigInteger num2 = new BigInteger ("2");
		BigInteger num3 = new BigInteger ("0");
		BigInteger num4 = new BigInteger ("0");
		String check;
		Boolean test = false;
		
		num1.valueOf(1);
		num2.valueOf(2);
		num3.valueOf(0);
		num4.valueOf(0);
		
		while (test == false)
		{
			num3 = num1.add(num2);
			num4 = num3.add(num2);
			num1 = num3.add(num4);
			num2 = num4.add(num1);
			
			check = num1.toString();
			if (check.length()>=1000)
			{
				System.out.println(num1);
			}
			check = num2.toString();
			if (check.length()>=1000)
			{
				System.out.println(num2);
			}
			check = num3.toString();
			if (check.length()>=1000)
			{
				System.out.println(num3);
			}
			check = num4.toString();
			if (check.length()>=1000)
			{
				System.out.println(num4);
				test = true;
			}
		}
	}
}
[/php]
Okay so I took you're BigInteger lines, and that allowed it to compile without error, but I seem to be getting a wrong answer nonetheless. Also. why is "BigInteger num1 = new BigInteger ("1");" necessary? What was wrong with the way I was trying to declare them before?

---

### Post by Lster on 2008-05-17
What answer do you get? (I can see how close you are...)

---

### Post by rye_ on 2008-05-17
You do know that my code works? Perhaps compile that to give you the solution your need to work towards

---

### Post by DanielJackins on 2008-05-17
```
1070066266382758936764980584457396885083683896632151665013235203375314520604694040621889147582489792657804694888177591957484336466672569959512996030461262748092482186144069433051234774442750273781753087579391666192149259186759553966422837148943113074699503439547001985432609723067290192870526447243726117715821825548491120525013201478612965931381792235559657452039506137551467837543229119602129934048260706175397706847068202895486902666185435124521900369480641357447470911707619766945691070098024393439617474103736912503231365532164773697023167755051595173518460579954919410967778373229665796581646513903488154256310184224190259846088000110186255550245493937113651657039447629584714548523425950428582425306083544435428212611008992863795048006894330309773217834864543113205765659868456288616808718693835297350643986297640660000723562917905207051164077614812491885830945940566688339109350944456576357666151619317753792891661581327159616877487983821820492520348473874384736771934512787029218636250627816
```
is what I'm getting. I'll give you're code a try rye.

EDIT: Whoops! Passed over the fact that I'm trying to find which term that is, not the number. My mistake!

---

### Post by Lster on 2008-05-17
Congrats. :)

---

### Post by rye_ on 2008-05-17
EDIT : I SEE ABOVE YOU SPOTTED THIS AND THIS POST IS IRRELEVANT.
EDIT2: Since your on the right track now, I'll consider this thread solved and will stop watching.  best of luck Daniel


There's a mistake in your premise.
The problem is not asking for the first number in the fibonacci series with 1000 digits, instead it asks for the first term that has 1000 digits.

e.g. in series 1,2,4,8,16, the term which equals 16 is 5.

Ryan

---

### Post by DanielJackins on 2008-05-17
Thank you all for you're help, I got the answer :) I'll marked the thread as solved, but I still don't see why I couldn't just declare them as simply BigInteger

---

### Post by achelis on 2008-05-17
I take it you're asking why the following code didn't work?

```

        BigInteger num1; 
        BigInteger num2;
        BigInteger num3;
        BigInteger num4;
        String check;
        Boolean test = false;
        
        num1.valueOf(1);
        num2.valueOf(2);
        num3.valueOf(0);
        num4.valueOf(0); 

```

I'll try to explain... The compiler complained that num1 et.c. was not initialized. They were declared but was never assigned a value. Therefore you could not call a method on them ( num1.valueOf(1) calls the method valueOf(1) on the object num1 - which was not initilized...)

Second mistake... valueOf(1) is a static method that returns a BigInteger. To use it you should have done something like this:

```

        num1 = BigInteger.valueOf(1);

```

That would assign the variable num1 to the object returned by the method valueOf...

hope this makes sense.

---

