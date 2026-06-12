---
title: "Jave math loop help!"
date: 2010-03-01
forum: Programming Talk
---

### Post by Michaeljs1990 on 2010-03-01
OK this is a math program i have been working on a little bit but i am at a loss for a solution to this problem right now. Skip this next chunk of code if you would like, I targeted the main problem after it.
```

package javaapplication1;

/********************************************
*Michael Schuett
*2/25/10
*Java
*This is my first semi-big java program
***********************************************/
import java.util.Scanner;

public class Main
{
    public static void main(String[] args)
    {
        String input;

    Scanner stdIn = new Scanner(System.in);

    System.out.println("Hello, Welcome to MMath Beta 0.1");
    System.out.println("What would you like to do? (for help enter h): ");
    input = stdIn.next();
    if (input.equals("h"))
        {
        System.out.print("type in add to add or subtract numbers." + '\n');
        System.out.print("type in mult to multiply or divide."     + '\n');
        System.out.print("only 2 currently available in Beta 0.1"  + '\n');
        }
        if (input.equals("add"))
                {
            int count = 0;
            double fNum;
            double fNumI;
            while (count == 0)
            {
                System.out.print("Enter the numbers you would like to add" + '\n');
                fNum = stdIn.nextDouble();
                fNumI = stdIn.nextDouble();
            
                    while (count == 0)
                        {
                        double nNum;
                        String inputtwo;
                        System.out.println("would you like to add another number?");
                        inputtwo = stdIn.next();
                        nNum = fNum + fNumI;
                            if (inputtwo.equalsIgnoreCase("y"))
                        {
                                double fNumII;
                                fNumII = stdIn.nextDouble();
                                nNum = nNum + fNumII;
                        }//end of if "y"
                            else if (inputtwo.equalsIgnoreCase("no"))
                            {
                                System.out.println("this equals: " + (nNum));
                                count ++;
                            }//end of else if statement
                        }//end of while count = 0
            }//end of while statement
        }//end of if "add" statement
        }//end of public static void main
    }//end of public class main

```OK i know i have not worked out all the bugs or even made the commands the user inputs optimal yet. however thats another story lol. My main problem is i am trying to add my variable fNumII to the total of nNum but i am having a hard time seeing how to do this. So far the code "works" it runs and responds right until you say no and the answer it outputs only includes fNum and fNumI. 

_ALSO what i want the program to do is to keep letting the user add numbers as many times as they want  that is my target goal._

here is the problem's exact location... i think.
```

while (count == 0)
                        {
                        double nNum;
                        String inputtwo;
                        System.out.println("would you like to add another number?");
                        inputtwo = stdIn.next();
                        nNum = fNum + fNumI;
                            if (inputtwo.equalsIgnoreCase("y"))
                        {
                                double fNumII;
                                fNumII = stdIn.nextDouble();
                                nNum = nNum + fNumII;
                        }//end of if "y"
                            else if (inputtwo.equalsIgnoreCase("no"))
                            {
                                System.out.println("this equals: " + (nNum));
                                count ++;
                            }//end of else if statement
                        }//end of while count = 0

```i hope my code has some readability to everyone. thanks:KS

---

### Post by azagaros on 2010-03-01
[PHP]
bool myContinue = TRUE;
double nNum = 0.0;
while (myContinue)
{
    String inputtwo;
    System.out.println("would you like to add another number?");
    inputtwo = stdIn.next();
    if (inputtwo.equalsIgnoreCase("Y"))
    {
        double fNumII;
        fNumII = stdIn.nextDouble();
        nNum = nNum + fNumII;
    }//end of if "y"
    else
    {
        if (inputtwo.equalsIgnoreCase("no"))
        {
            System.out.println("this equals: " + (nNum));
            myContinue = FALSE;
        }//end of if "no"
    } // end of Condition "Y"
}// end of while
[/PHP]

this code model might fit what your trying to do better.  I think you init'd the sum var every time you cycled the loop.

---

### Post by Michaeljs1990 on 2010-03-01
Thank you azagaros! that was it every time i looped through it was setting it back to the original value. i set nNum = fNum + fNumI; outside of the second while loop and it works!

here is the fixed code for anyone who cares :)

```

package javaapplication1;

/********************************************
*Michael Schuett
*2/25/10
*Java
*This is my first semi-big java program
***********************************************/
import java.util.Scanner;

public class Main
{
    public static void main(String[] args)
    {
        String input;

    Scanner stdIn = new Scanner(System.in);

    System.out.println("Hello, Welcome to MMath Beta 0.1");
    System.out.println("What would you like to do? (for help enter h): ");
    input = stdIn.next();
    if (input.equals("h"))
        {
        System.out.print("type in add to add or subtract numbers." + '\n');
        System.out.print("type in mult to multiply or divide."     + '\n');
        System.out.print("only 2 currently available in Beta 0.1"  + '\n');
        }
        if (input.equals("add"))
                {
            int count = 0;
            double fNum;
            double fNumI;
            double nNum;
            while (count == 0)
            {
                System.out.print("Enter the numbers you would like to add" + '\n');
                fNum = stdIn.nextDouble();
                fNumI = stdIn.nextDouble();
                nNum = fNumI + fNum;
            
                    while (count == 0)
                        {
                        String inputtwo;
                        System.out.println("would you like to add another number?");
                        inputtwo = stdIn.next();
                            if (inputtwo.equalsIgnoreCase("y"))
                        {
                                double fNumII;
                                fNumII = stdIn.nextDouble();
                                nNum = nNum + fNumII;
                        }//end of if "y"
                            else if (inputtwo.equalsIgnoreCase("no"))
                            {
                                System.out.println("this equals: " + (nNum));
                                count ++;
                            }//end of else if statement
                        }//end of while count = 0
            }//end of while statement
        }//end of if "add" statement
        }//end of public static void main
    }//end of public class main

```

---

