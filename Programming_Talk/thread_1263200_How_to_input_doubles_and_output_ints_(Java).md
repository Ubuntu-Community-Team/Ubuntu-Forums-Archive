---
title: "How to input doubles and output ints (Java)"
date: 2009-09-10
forum: Programming Talk
---

### Post by s3a on 2009-09-10
The following is my code:

```
import java.util.Scanner;



public class Assignment_2A



	{



		public static void main (String [] args)



			{



				Scanner kb;

				kb = new Scanner(System.in);



				System.out.print("Enter the Year, Month and Day: ");



					double year = kb.nextDouble();

					double month = kb.nextDouble();

					double day = kb.nextDouble();				

				{	

					if(year < 1582)

						System.out.println("Invalid year");

					

					if(month < 1)

						System.out.println("Invalid month");

					

					if(month > 12)

						System.out.println("Invalid month");

					

					/* Figure out what to do for the fact that months can be 30 or 31 days

					   so that it can say invalid day if a number 31 is entered on a month

					   that has only 30 days. */

					

					if (day > 31)

					

					{

						System.out.println("Invalid day");

						System.exit(0);

					}

					

					if (day < 1)

					

					{

						System.out.println("Invalid day");

						System.exit(0);

					}

										

					if(month == 1)

						System.out.print("January, " + day + ", " + year);

					

					if(month == 2)

						System.out.print("February, " + day + ", " + year);

					

					if(month == 3)

						System.out.print("March, " + day + ", " + year);

					

					if(month == 4)

						System.out.print("April, " + day + ", " + year);

					

					if(month == 5)

						System.out.print("May, " + day + ", " + year);

					

					if(month == 6)

						System.out.print("June, " + day + ", " + year);

					

					if(month == 7)

						System.out.print("July, " + day + ", " + year);

					

					if(month == 8)

						System.out.print("August, " + day + ", " + year);

					

					if(month == 9)

						System.out.print("September, " + day + ", " + year);

					

					if(month == 10)

						System.out.print("October, " + day + ", " + year);

					

					if(month == 11)

						System.out.print("November, " + day + ", " + year);

					

					if(month == 12)

						System.out.print("December, " + day + ", " + year);

					

				}





			}



	}

```

If this seems very repetitive, it's because my teacher didn't teach us "shortcuts." In fact, he said that he would talk about better ways of doing this repetitive assignment later.

_My question is:_
I made it so that the user can input a double but if at least one of the numbers inputed is a double then the date printed will be in double form (with decimals). I know it is useless to receive doubles if there is no need to output a double but I want the program to be able to receive doubles and reject them with an error message (that I already have created). **So how do I force the output to be in integer form?**

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by Reiger on 2009-09-10
You may want to read up on type casts (Java type casts); alternatively you may want to use format strings (String.format) or for another option you can simply reject doubles from the user input since they don't make any sense anyway. (I have yet to see a form where people were allowed to write down their date of birth as: &#8220;19.75 - 2.3 - 1989.00&#8221;)

---

### Post by s3a on 2009-09-10
Yes but like I said I'd still like it to reject the input which it does but if you put a proper input, the output is in double form.

---

### Post by Reiger on 2009-09-10
Your code is not rejecting doubles at all:
```

double year = kb.nextDouble();
double month = kb.nextDouble();
double day = kb.nextDouble();

```

Your if() logic does not reject doubles. It merely compares them against integers but if the equality holds you still have doubles as your data. Fundamentally if() statements themselves do not alter your input data (it'd be most inconvenient if they did) and your output methods use default string representations. Thus you need to either type cast your data to another type with different string representation, use output formatting or other modifications to output Strings to hide the fact that they are doubles, or get rid of the doubles altogether and replace them with something of a different (more suitable) type.

---

### Post by shadylookin on 2009-09-10
your code would work if you used integers. In fact it doesn't really make any sense to allow someone to input 25000.2 years, 11.3 months, or 4.2 days. Also Any specific reason you've blocked your if statements in?

Anyway for your question at hand you could just cast your doubles as ints

```

int year = (int)kb.nextDouble();

int month = (int)kb.nextDouble();

int day = (int)kb.nextDouble();

```

---

### Post by s3a on 2009-09-10
> **shadylookin said:**
> your code would work if you used integers. In fact it doesn't really make any sense to allow someone to input 25000.2 years, 11.3 months, or 4.2 days. Also Any specific reason you've blocked your if statements in?

Anyway for your question at hand you could just cast your doubles as ints

```

int year = (int)kb.nextDouble();

int month = (int)kb.nextDouble();

int day = (int)kb.nextDouble();

```

Thanks that's just what I needed! :D

---

### Post by s3a on 2009-09-10
To answer the other questions:

By reject I meant a "rejecting" output message not a part of the code.

As for the blocking my if statements is what I just commented out what you're referring to?

```
import java.util.Scanner;



public class Assignment_2A



	{



		public static void main (String [] args)



			{



				Scanner kb;

				kb = new Scanner(System.in);



				System.out.print("Enter the Year, Month and Day: ");



					int year = (int)kb.nextDouble();

					int month = (int)kb.nextDouble();

					int day = (int)kb.nextDouble();				

				//{	

					if(year < 1582)

						System.out.println("Invalid year " + year);

					

					if(month < 1)

						System.out.println("Invalid month " + month);

					

					if(month > 12)

						System.out.println("Invalid month " + month);

					

					/* Figure out what to do for the fact that months can be 30 or 31 days

					   so that it can say invalid day if a number 31 is entered on a month

					   that has only 30 days. */

					

					if (day > 31)

					

					{

						System.out.println("Invalid day");

						System.exit(0);

					}

					

					if (day < 1)

					

					{

						System.out.println("Invalid day");

						System.exit(0);

					}

										

					if(month == 1)

						System.out.print("January, " + day + ", " + year);

					

					if(month == 2)

						System.out.print("February, " + day + ", " + year);

					

					if(month == 3)

						System.out.print("March, " + day + ", " + year);

					

					if(month == 4)

						System.out.print("April, " + day + ", " + year);

					

					if(month == 5)

						System.out.print("May, " + day + ", " + year);

					

					if(month == 6)

						System.out.print("June, " + day + ", " + year);

					

					if(month == 7)

						System.out.print("July, " + day + ", " + year);

					

					if(month == 8)

						System.out.print("August, " + day + ", " + year);

					

					if(month == 9)

						System.out.print("September, " + day + ", " + year);

					

					if(month == 10)

						System.out.print("October, " + day + ", " + year);

					

					if(month == 11)

						System.out.print("November, " + day + ", " + year);

					

					if(month == 12)

						System.out.print("December, " + day + ", " + year);

					

				//}



			if(month == 1)

			System.out.println();

			System.out.println("Day number: " + day);



			// The following yields APPROXIMATE results and needs to be fixed.



			if(month == 2)

			System.out.println("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 3)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 4)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 5)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 6)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 7)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 8)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 9)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 10)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 11)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 12)

			System.out.print("Day number: " + ((month * 30) - 30 + day));



			}



	}
```

---

### Post by dwhitney67 on 2009-09-10
> **Reiger said:**
> You may want to read up on type casts (Java type casts); alternatively you may want to use format strings (String.format) or for another option you can simply reject doubles from the user input since they don't make any sense anyway. (I have yet to see a form where people were allowed to write down their date of birth as: &#8220;19.75 - 2.3 - 1989.00&#8221;)

I've been consuming a wee bit too much of the liquid form of my avatar, and yet at the first glance of the code from the OP, I drew the same conclusion.

Why is someone attempting to read double values for the year, month, and day?

The example from the 3rd paragraph of this page sums up what is required... [http://java.sun.com/javase/6/docs/api/java/util/Scanner.html](http://java.sun.com/javase/6/docs/api/java/util/Scanner.html)

---

### Post by dwhitney67 on 2009-09-10
> **s3a said:**
> To answer the other questions:

By reject I meant a "rejecting" output message not a part of the code.

As for the blocking my if statements is what I just commented out what you're referring to?


Hint:

```

if (someConditionIsTrue)
{
   ... then do this
}
else if (someOtherConditionIsTrue)
{
   ... then do this other thing
}
...
else
{
   ... damn, if it is not any of the above, it must be this!
}

```

---

### Post by shadylookin on 2009-09-10
> **s3a said:**
> To answer the other questions:

By reject I meant a "rejecting" output message not a part of the code.

As for the blocking my if statements is what I just commented out what you're referring to?

```
import java.util.Scanner;



public class Assignment_2A



	{



		public static void main (String [] args)



			{



				Scanner kb;

				kb = new Scanner(System.in);



				System.out.print("Enter the Year, Month and Day: ");



					int year = (int)kb.nextDouble();

					int month = (int)kb.nextDouble();

					int day = (int)kb.nextDouble();				

				//{	

					if(year < 1582)

						System.out.println("Invalid year " + year);

					

					if(month < 1)

						System.out.println("Invalid month " + month);

					

					if(month > 12)

						System.out.println("Invalid month " + month);

					

					/* Figure out what to do for the fact that months can be 30 or 31 days

					   so that it can say invalid day if a number 31 is entered on a month

					   that has only 30 days. */

					

					if (day > 31)

					

					{

						System.out.println("Invalid day");

						System.exit(0);

					}

					

					if (day < 1)

					

					{

						System.out.println("Invalid day");

						System.exit(0);

					}

										

					if(month == 1)

						System.out.print("January, " + day + ", " + year);

					

					if(month == 2)

						System.out.print("February, " + day + ", " + year);

					

					if(month == 3)

						System.out.print("March, " + day + ", " + year);

					

					if(month == 4)

						System.out.print("April, " + day + ", " + year);

					

					if(month == 5)

						System.out.print("May, " + day + ", " + year);

					

					if(month == 6)

						System.out.print("June, " + day + ", " + year);

					

					if(month == 7)

						System.out.print("July, " + day + ", " + year);

					

					if(month == 8)

						System.out.print("August, " + day + ", " + year);

					

					if(month == 9)

						System.out.print("September, " + day + ", " + year);

					

					if(month == 10)

						System.out.print("October, " + day + ", " + year);

					

					if(month == 11)

						System.out.print("November, " + day + ", " + year);

					

					if(month == 12)

						System.out.print("December, " + day + ", " + year);

					

				//}



			if(month == 1)

			System.out.println();

			System.out.println("Day number: " + day);



			// The following yields APPROXIMATE results and needs to be fixed.



			if(month == 2)

			System.out.println("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 3)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 4)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 5)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 6)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 7)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 8)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 9)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 10)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 11)

			System.out.print("Day number: " + ((month * 30) - 30 + day));

			

			if(month == 12)

			System.out.print("Day number: " + ((month * 30) - 30 + day));



			}



	}
```



that's what I was talking about yes. Random blocking of java code is rather distracting in my opinion and I've never seen it done by anyone other than you. 

Of course Dwhitney67 is also correct in that your if statements could be done better. Because regardless of whether the month is 1 you're forcing it to check through all the other 11 months. 

it should be

[PHP]
if(month == 1){
    January
} 

else if(month == 2){
    February 
}

else if(month ==3){
    March
}

...so on and so forth...

else if(month = 12){
   December
} 

else{
    System.out.print("you're an idiot for putting in an incorrect month")
}

[/PHP]

it's not really a big deal on such a small program, but you might as well learn the proper way now. Plus if you did it that way then you could even get rid of your month checking here

```

if(month < 1)

						System.out.println("Invalid month " + month);

					

					if(month > 12)

						System.out.println("Invalid month " + month);

					

```

---

### Post by dwhitney67 on 2009-09-11
Undoubtedly the exercise is to get the programmer to familiarize themselves with if-statements, and perhaps else-if-statements, and perhaps switch-statements.

With respect to gathering input, DON'T use nextDouble(); use nextInt().

If the user makes an input mistake, give them another opportunity to enter the correct input... don't just kill the app... that's lame.

Here's a shot at the solution (note, there are probably built-in utilities within the Java library suite that handle all of this):
```

import java.util.Scanner;

public class MyDate
{
   private Scanner kb;

   private int MD_YEAR  = 0;
   private int MD_MONTH = 1;
   private int MD_DAY   = 2;

   private String month[] = { "January", "February", "March", "April",
                              "May", "June", "July", "August", "September",
                              "October", "November", "December" };

   private int monthDay[] = { 31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31 };

   MyDate() {
      kb = new Scanner(System.in);
   }

   private boolean dateValueEval(int value, int minValue) {
      return value >= minValue;
   }

   private boolean dateValueEval(int value, int minValue, int maxValue) {
      return value >= minValue && value <= maxValue;
   }

   public int getInput(String prompt, int minValue) {
      int input = 0;

      while (true) {
         System.out.print(prompt);
         input = kb.nextInt();

         if (dateValueEval(input, minValue)) break;

         System.out.println("Error:  Value must be >= " + minValue + ".\n");
      }

      return input;
   }

   public int getInput(String prompt, int minValue, int maxValue) {
      int input = 0;

      while (true) {
         System.out.print(prompt);
         input = kb.nextInt();

         if (dateValueEval(input, minValue, maxValue)) break;

         System.out.println("Error:  Value must be >= " + minValue + " and <= " + maxValue + ".\n");
      }

      return input;
   }

   public void displayDate(int yyyy, int mm, int dd) {
      System.out.println("Calendar Date: " + month[mm - 1] + " " + dd + ", " + yyyy);
   }

   public void displayDayNumber(int mm, int dd) {
      int dayOfYear = 0;

      for (int m = 0; m < mm; ++m) dayOfYear += monthDay[m];

      System.out.println("Day of Year: " + (dayOfYear + dd));
   }

   public static void main(String[] args) {
      MyDate md = new MyDate();

      int year  = md.getInput("Enter the year: ",  1582);
      int month = md.getInput("Enter the month: ", 1, 12);
      int day   = md.getInput("Enter the day: ",   1, 31);

      md.displayDate(year, month, day);
      md.displayDayNumber(month, day);
   }
}

```

Now I am off to work... albeit an hour late.  The price I pay to help others.

---

