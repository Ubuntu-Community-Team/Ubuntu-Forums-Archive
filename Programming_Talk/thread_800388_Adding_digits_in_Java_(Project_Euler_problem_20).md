---
title: "Adding digits in Java (Project Euler problem 20)"
date: 2008-05-19
forum: Programming Talk
---

### Post by DanielJackins on 2008-05-19
I've been trying to solve Problem 20 on Project Euler and here is my code henceforth;
[php]/*n! means n × (n &#8722; 1) × ... × 3 × 2 × 1

Find the sum of the digits in the number 100!*/

import java.math.*;

public class Sum
{
	public static void main (String[] args)
	{
		BigInteger sum = new BigInteger("1");
		int num = 1;
		BigInteger inc = new BigInteger("1");
		BigInteger count = new BigInteger("1");
		String add;
		int count2 = 0;
		int sum2 = 0;
		
		
		while (num <= 100)
		{
			sum = sum.multiply(count);
			System.out.println(sum);
			count = count.add(inc);
			num++;
		}
		
		add = sum.toString();
		while (count2 < 500);
		{
			sum2 += add.charAt(count2);
			count2++;
			System.out.println(sum2);
		}
		
	}
}
[/php]

So the first part of my code works fine, and finds the product, but the second part where I'm attempting to add the digits doesn't give any output. I don't know if I'm even doing it the right way, I was just giving that way a shot. Why doesn't my second loop work?

---

### Post by dwhitney67 on 2008-05-19
For starters, remove the semi-colon after the 2nd loop statement.

[PHP]        while (count2 < 500);  <--- here![/PHP]

---

### Post by NormR2 on 2008-05-19
Why do you say it doesn't work?
Do you get an error message or invalid output or what?
Please post your console output that shows what's wrong with a description of why you think it's wrong.

---

### Post by DanielJackins on 2008-05-19
Okay, so removing the semi-colon (stupid mistake =( ) did better, but now I get this message while the program is adding the digits; Exception in thread "main" java.lang.StringIndexOutOfBoundsException: String index out of range: 158
	at java.lang.String.charAt(String.java:694)
	at Sum.main(Sum.java:31)
The program compiles fine, though.

---

### Post by dwhitney67 on 2008-05-19
Since by now you have encountered the crash due to exceeding the bounds of the string 'add', I decided to correct the problem.

Here's my solution.  Please let me know if this fulfills the requirements of the problem.
[PHP]/*n! means n × (n &#8722; 1) × ... × 3 × 2 × 1

Find the sum of the digits in the number 100!*/

import java.math.BigInteger;
import java.lang.Character;

public class Sum
{
    public static void main (String[] args)
    {
        BigInteger ONE   = new BigInteger("1");
        BigInteger sum   = new BigInteger("1");
        BigInteger count = new BigInteger("1");

        while (count.longValue() <= 100)
        {
            sum = sum.multiply(count);
            count = count.add(ONE);

            System.out.println(sum);
        }
        System.out.println();


        String add = sum.toString();
        int sum2   = 0;

        for (int i = 0; i < add.length(); ++i)
        {
            sum2 += Character.getNumericValue( add.charAt(i) );
        }
        System.out.println(sum2);
    }
}[/PHP]

P.S.  In the future, when you work on a similar type of problem, try to start off with a small number, say 5, in lieu of 100.  It is easier to work towards the solution.

---

### Post by DanielJackins on 2008-05-19
Thank you for you're help, I took you're Character thing and it worked perfectly. Does String just not support numbers that big?

---

### Post by dwhitney67 on 2008-05-19
The Character.getNumericValue() is a static method of the Character class.  

It converts a single character (that hopefully represents a digit from 0-9) into an integer value; it does not work on an entire string... which in the case of 100! is huge.  Hence the reason for the loop to get each individual character of the string.

P.S.  I'm sure there is a better way to do this stuff.  I haven't programmed in Java in a couple of years.

---

### Post by DanielJackins on 2008-05-19
That makes sense, thanks a bunch for you're help :)

---

### Post by achelis on 2008-05-20
The reason this part didn't work as expected:
```

           sum2 += add.charAt(count2); 

```

You're casting the char to an int. In Java this is done by returning the ASCII(or Unicode) value of the char. To convert back to a 'normal' number you could subtract 48. The previous method posted is recommended however as it will give you a proper error message if you try to parse a char that is not a number. Integer.parseInt(String s) is another option.

When writing code like this it's a good idea to split the tasks into different methods. That way you can test the tasks separately.

A quick example to show what I mean (the code is pretty much the same as was posted earlier, only I extracted two methods)

```

	public static void main(String[] args)
	{		
		BigInteger n = factorial(100);

		int result = addDigits(n);

		System.out.println(result);			
	}

	private static BigInteger factorial(int n)
	{
		BigInteger sum = BigInteger.valueOf(1);

		int i = 1;
		while (i <= n)
		{
			sum = sum.multiply(BigInteger.valueOf(i));
			i++;
		}
		return sum;
	}

	private static int addDigits(BigInteger sum)
	{
		int result = 0;
		String strSum = sum.toString();
		for(int i = 0;i < strSum.length(); i++)			
		{
			result += Integer.parseInt(strSum.charAt(i) + "");
		}
		return result;
	}

```

Oh, and String doesn't support numbers at all - it represents, well, a string of characters. 

And lastly, when not parsing a String I'd recommend using BigInteger.valueOf(number) over new BigInteger("number");

The reason there is no constructor taking an int or long was a decision made for performance reasons, hence the static valueOf-method instead.

---

