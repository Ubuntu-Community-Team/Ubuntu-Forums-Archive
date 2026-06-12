---
title: "I know how to use the switch statement with integers but need help for letters!"
date: 2009-09-17
forum: Programming Talk
---

### Post by s3a on 2009-09-17
The part in bold is the part I am having trouble with. What I am trying to do is this: If you don't do stupidities, you could enter 2009 9 17 for example and it will print the date, etc. Not so long ago, I had it set up successfully (no switch statement) so that if someone were to type lets say 2k9 9 17 it would print *Invalid "2k9"* and stuff like that. But if the user enters like 2009 nine 17, the program would get "confused" and crash. I'm reading my book which seems to indicate that case 0:, case 1:, case 2:, etc is for integers (as suggested also by the compilation error) and you need to do something a little different for letters.

I would very much appreciate it if someone could modify my code and paste it all back in a code window so that I can see how it works.

The following is my code:

```
import java.util.Scanner;



public class Assignment_2A



	{



		public static void main (String [] args)



		{



				Scanner kb = new Scanner(System.in);



				System.out.print("Enter the Year, Month and Day: ");



[B]				if(! kb.hasNextInt())

					{

					String junk = kb.next();

					

					switch(junk)

					

					{

					case 1:

					

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					break;

					

					case 2:

					

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					break;

					

					case 3:

					

					System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);

					break;[/B]

					

					

					

					/*System.out.println("Invalid " + "\"" + junk + "\"");

					System.out.println("Must be an Integer." + "\n" + "Bye.");

					System.exit(0);*/

					

					}

					}



					/* What do I modify so that the user can input anything and so that if it's a number, the calculations will follow

					like normal but if it's letters, there will be a System.out.print(); error message? */



					int year = (int)kb.nextDouble();

					int month = (int)kb.nextDouble();

					int day = (int)kb.nextDouble();



					/* leap year if year is divisible by 4 AND is not century year

					OR if it is divisible by 400 (explanation of the following leap year statement) */



					boolean isLeapYear = (year % 400 == 0) && (year % 100 != 0) || (year % 4 == 0);



					if(year < 1582)

					{

						System.out.println("Invalid year " + "\"" + year + "\"");

						System.exit(0);

					}



					if((month < 1) || (month > 12))

						{

						System.out.println("Invalid month " + month);

						System.exit(0);

						}



					/* Figure out what to do for the fact that months can be 30 or 31 days

					   so that it can say invalid day if a number 31 is entered on a month

					   that has only 30 days. */



					if ((day > 31) & (day < 1))



					{

						System.out.println("Invalid day " + "\"" + day + "\"");

						System.exit(0);

					}





					//if(month == 1)

					//	System.out.print("Date: January, " + day + ", " + year);

/*

					if((month == 2) && (isLeapYear == true) && ((day > 29) || (day < 1)))

						{

						System.out.println("Invalid day " + "\""	+ day + "\"");

						System.exit(0);

						}

					else if(month == 2)

						System.out.print("Date: February, " + day + ", " + year);

*/

					switch(month)

					{

						case 1: System.out.print("Date: January, " + day + ", " + year);

								System.out.println("\n" + "Day number: " + day); break;



						case 2: if((((isLeapYear == true) && ((day > 29) || (day < 1)))) || ((isLeapYear == false) && (day > 28)))

								{

									System.out.println("Invalid day " + "\""	+ day + "\"");

									System.exit(0);

								}

								else

									System.out.print("Date: February, " + day + ", " + year); 

								// The following line is not part of the conditional statement.

									System.out.println("\n" + "Day number: " + (31 + day)); break;



						case 3:

							System.out.print("Date: March, " + day + ", " + year);

							

							if(isLeapYear == true)

							System.out.println("\n" + "Day number: " + (31 + 29 + day));

							

							else

							System.out.println("\n" + "Day number: " + (31 + 28 + day));

							

							break;

							

						case 4:

							System.out.print("Date: April, " + day + ", " + year);

							

							if(isLeapYear == true)

							System.out.print("\n" + "Day number: " + ((31 + 29 + 31) + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + day)); break;

							

						case 5:

							System.out.print("Date: May, " + day + ", " + year);

							

							if(isLeapYear == true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + day));

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + day));

							

							break;

							

						case 6:

							System.out.print("Date: June, " + day + ", " + year);

							

							if(isLeapYear = true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + day));

							

							break;

							

						case 7:

							System.out.print("Date: July, " + day + ", " + year);

							

							if(isLeapYear = true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + 30 + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + 30 + day));

							

							break;

							

						case 8:

							System.out.print("Date: August, " + day + ", " + year);

							

							if(isLeapYear = true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + 30 + 31 + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + 30 + 31 + day));

							

							break;

							

						case 9:

							System.out.print("Date: September, " + day + ", " + year);

							

							if((month == 9) && (isLeapYear = true))

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + 30 + 31 + 31 + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + 30 + 31 + 31 + day));

							

							break;

							

						case 10:

							System.out.print("Date: October, " + day + ", " + year);

							

							if(isLeapYear = true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + 30 + 31 + 31 + 30 + day));

						

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + 30 + 31 + 31 + 30 + day));

							

							break;

							

						case 11:

							System.out.print("Date: November, " + day + ", " + year);

							

							

							if(isLeapYear = true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + 30 + 31 + 31 + 30 + 31 + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + 30 + 31 + 31 + 30 + 31 + day));

							

							break;

							

						case 12:

							System.out.print("Date: December, " + day + ", " + year);

							

							if(isLeapYear = true)

							System.out.print("\n" + "Day number: " + (31 + 29 + 31 + 30 + 31 + 30 + 31 + 31 + 30 + 31 + 30 + day));

							

							else

							System.out.print("\n" + "Day number: " + (31 + 28 + 31 + 30 + 31 + 30 + 31 + 31 + 30 + 31 + 30 + day));

							

							break;

					}

		}



	}
```

Thanks in advance!

---

### Post by s3a on 2009-09-17
Actually I don't want to use the switch statement, instead I want it to just take the first 3 inputted strings (seperated by a space).

---

### Post by dwhitney67 on 2009-09-17
To parse the input of 3 words, perhaps you can try something similar to this:
```

import java.util.Scanner;
import java.lang.Exception;

public class ScanWord
{
   public static void main(String[] args)
   {
      try {
         Scanner kb = new Scanner(System.in);

         System.out.print("Enter 3 words: ");

         String word1 = kb.next("\\p{Alpha}+\\b");
         String word2 = kb.next("\\p{Alpha}+\\b");
         String word3 = kb.next("\\p{Alpha}+");

         System.out.println("Echoing input: " + word1 + " " + word2 + " " + word3);
      }
      catch (Exception e) {
         System.out.println("Exception: " + e.toString());
      }
   }
}

```

P.S.  If you haven't already, bookmark this page:  [http://java.sun.com/javase/6/docs/api/](http://java.sun.com/javase/6/docs/api/)

---

