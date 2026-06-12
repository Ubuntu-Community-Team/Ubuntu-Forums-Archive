---
title: "Simple Java programming Question (I am a beginner)"
date: 2009-08-29
forum: Programming Talk
---

### Post by s3a on 2009-08-29
_Ok so here is what I have done:_

[i]import java.util.Scanner;
public class UnitConverter
   {
      public static void main (String [] args)
      { //create a new scanner object and connect it to the computer

      Scanner kb;
      kb = new Scanner (System.in);
      //Prompt user to enter a number of seconds
      System.out.print("Enter a number of seconds: ");
      int SECONDS = kb.nextInt();
      [color=#FF0000]final[/color] int MINUTES = (SECONDS) / (60);
      [color=#FF0000]final[/color] int HOURS = (SECONDS) / (3600);
      [color=#FF0000]final[/color] int DAYS = (SECONDS) / (3600*24);
      System.out.println(SECONDS + " Seconds ");
      System.out.println(MINUTES + " Minutes ");
      System.out.println(HOURS +" Hours ");
      System.out.println(DAYS + " Days");
      System.out.println(); //skip line
      } // for main()
   } //for class UnitConverter[/i]

When you enter a number such as 106478 seconds, you receive the equivalent of that number in seconds, minutes, hours and days. However, this is NOT what I want to accomplish. What I want is for it to tell me how many days that is and how many additional hours, minutes and seconds it is TO THAT DAY.

My teacher said that the output should be:

Days: 1
Hours: 5
Minutes: 34
Seconds: 38

_However I get:_
Seconds: 106478
Minutes: 1774
Hours: 29
Days: 1

How do I make it so the output is what my teacher expects? Also what difference does it make if the world [color=#FF0000]final[/color] is there or not? I know I might be asking very simple questions but I just started and I will eventually be helping the free software movement so please bear with me.

Any help would be GREATLY appreciated!
Thanks in advance!

---

### Post by sim_mmm on 2009-08-29
You should use the rest of the division given by the operator modulo (%)

So basicly :

106478 / (3600*24) = Nb day
106478 % (3600*24) = Rest of the division that you use to determine Nb Hours

You must determine the element in the correct order Days, Hours, Minutes, Seconds. And you should use the rest of the previous devision to calcul the current element.

I add Spreadsheets to the message to show you in exemple of what kind of formula your should use.

---

### Post by baizon on 2009-08-29
> **s3a said:**
> 
How do I make it so the output is what my teacher expects? Also what difference does it make if the world [color=#FF0000]final[/color] is there or not? I know I might be asking very simple questions but I just started and I will eventually be helping the free software movement so please bear with me.


[http://en.wikipedia.org/wiki/Final_%28Java%29#Final_variables]("http://en.wikipedia.org/wiki/Final_%28Java%29#Final_variables")

> **s3a said:**
> 
When you enter a number such as 106478 seconds, you receive the equivalent of that number in seconds, minutes, hours and days. However, this is NOT what I want to accomplish. What I want is for it to tell me how many days that is and how many additional hours, minutes and seconds it is TO THAT DAY.


```

1 minute = 60 seconds
1 hour = 3,600 seconds
1 day = 86,400 seconds
1 week = 604,800 seconds
1 month = 2,592,000 seconds (30 days)
1 month = 2,678,400 seconds (31 days)
1 year = 31,536,000 seconds

```

```
import java.util.Scanner;
public class UnitConverter
{
public static void main (String [] args) {
	Scanner kb;
	kb = new Scanner(System.in);
	//Prompt user to enter a number of seconds
	System.out.print("Enter a number of seconds: ");
	int time = kb.nextInt();
	final int seconds = (int) (time % 60);
        final int minutes = (int) ((time / 60) % 60);
        final int hours = (int) ((time / 3600) % 24);
        final int days = (int) ((time / 86400) % 7);
	System.out.println(seconds + " Seconds ");
	System.out.println(minutes + " Minutes ");
	System.out.println(hours +" Hours ");
	System.out.println(days + " Days");
	} 
} //for class UnitConverter

```

I hope it helps.

---

### Post by s3a on 2009-08-29
Ok so:

import java.util.Scanner;
public class Ubuntu
{
public static void main (String [] args)
	{
	Scanner kb;
	kb = new Scanner(System.in);
	//Prompt user to enter a number of seconds
	System.out.print("How many seconds? ")
	System.out.println();
	int TIME_INPUT = kb.nextInt();
	[B]final int SECONDS = (int) (TIME_INPUT % 60);
        final int MINUTES = (int) ((TIME_INPUT / 60) % 60);
        final int HOURS = (int) ((TIME_INPUT / 3600) % 24);
        final int DAYS = (int) ((TIME_INPUT / 86400) % 7);[/B]
	System.out.println("Days: " + DAYS);
	System.out.println("Hours: " + HOURS);
	System.out.println("Minutes: " + MINUTES);
	System.out.println("Seconds: " + SECONDS);

	}
} //for class Ubuntu

(the formatting changed a bit when I copy pasted)

How can I make it so that there is an empty line after you enter the number of seconds and it gives you the output?

What about (int)(other_stuff) ----> is that multiplication or just stating that the time input is an integer or both?

Can someone explain the bold part especially the % in a little more detail please? I know what the % does like 10%3=1 for example but when it gets more complicated like that, I am confused and need explanation. My teacher gave me 2 problems like this to do for homework. This is the first one but I would like to go into extensive detail with this one until I feel I am ready to take on the second one which is a very similar program to build by myself.

Thanks!

---

### Post by soltanis on 2009-08-29
If I understand correctly, you do not know what the modulus operator does.

Modulus calculates the remainder after division of one integer by another. If you divide 10 by 3, in your example, the result is 9 with a remainder of 1. Notice that when you use modulus, the remainder will always be greater than or equal to zero and less than the divisor.

Practically speaking, modulus is used to find how much of a quantity is "left over". In your example,

seconds % 60

We use modulus here to find out the quantity of "how many seconds past the minute are we?" For an even quantity of seconds, like 120, we are exactly at 2 minutes. However, at 121 seconds, we are 1 second past 2 minutes: 121 % 60 = 1.

Similarly we find out how many minutes we have by doing the division:

seconds / 60 = minutes

Now to find the quantity "how many minutes past the hour are we?" we do the same thing as before:

minutes % 60 = (seconds / 60) % 60

Finally, for hours, we want "how many hours past the day are we?". Hours from seconds is

seconds / 3600 = hours

hours % 24 = (seconds / 3600) % 24 = (minutes / 60) % 24

---

### Post by Copernicus1234 on 2009-08-29
> What about (int)(other_stuff) ----> is that multiplication or just stating that the time input is an integer or both?

It converts the result from (other stuff) to a integer. 

```
final int DAYS = (int) ((TIME_INPUT / 86400) % 7);
```

If the result of the calculation ((TIME_INPUT / 86400) % 7) is a floating point number, you will get a error if trying to store it in DAYS if you dont convert it into a integer.

---

### Post by s3a on 2009-08-29
Ok I am beginning to understand this a bit better! Now I just need to understand why those specific numerical values were chosen after the % in my example code.

---

### Post by soltanis on 2009-08-29
Because there are:

60 seconds in a minute (for int seconds)
60 minutes in an hour (for int minutes)
24 hours in a day (for int hours)
7 days in a week (for int days)

So you see, those values should not exceed those maximums, which is why those numbers were chosen after the modulus.

---

