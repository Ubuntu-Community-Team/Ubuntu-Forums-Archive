---
title: "Creating a menu with Java"
date: 2009-09-12
forum: Programming Talk
---

### Post by Dark Aspect on 2009-09-12
Hello,

I am making an attempt to learn Java and I have created 4 very basic programs, one for each of the basic arithmetic operations. What I would like to do is create a menu that would look like this

```
Select an Application from below: 

(1) Addition
(2) Subtraction
(3) Multiplication
(4) Division 

Choice?:
```

However, I am not sure how to do this at this point. The only input I've used is input.nextInt(); for the Integers of each operation. Do I create a main class and have the four operations break off of that or can I integrate all four application in a single bytecode?

Here is a sample of my addition program:

```
import java.util.Scanner;

public class addition
{
	public static void main(String[] args)
	{
                System.out.println("Below is a simple sum = number1 + number2 Program \n");

                Scanner input = new Scanner( System.in );

                int number1;
                int number2;
                int sum;

                System.out.print( "Enter First integer: " );
                number1 = input.nextInt(); //Defines number1
                System.out.print( "Enter Second interger: " );
                number2 = input.nextInt(); //Defines number2

                sum = number1 + number2;
                System.out.printf( "Sum equals %d\n", sum);
	}
}

```

Any clue how to create a menu would be helpful, Should I define each menu option as an Integer?

---

### Post by shadylookin on 2009-09-12
create your main method to print out your options and take the user's choice

Then create addition, subtraction, division, and multiplication functions

[PHP]

public static void main(String args[]){
    System.out.println("1 add, 2 minus, 3 divide, 4 multiply");
    Scanner scan = new Scanner(System.in);
    int choice = scan.nextInt();
    if(choice == 1){
        addition();
    }
    else if(choice == 2){
        subtraction();
    }
    else if(choice == 3){
        division();
    }
    else if(choice == 4){
        multiplication();
    }
    else{
        System.out.println("not an option");
    }   

[/PHP]

now you can create your math functions

[PHP]
 public void addition(){
     Scanner input = new Scanner( System.in );
     int number1;
     int number2;
     int sum;

     System.out.print( "Enter First integer: " );
     number1 = input.nextInt(); //Defines number1
     System.out.print( "Enter Second interger: " );
     number2 = input.nextInt(); //Defines number2

     sum = number1 + number2;
     System.out.printf( "Sum equals %d\n", sum);
}

public void division(){
    //your division logic here
}

public void subtraction(){
    //your subtraction logic here
}

public void multiplication(){
    //your multiplication logic here
}

[/PHP]

---

### Post by issih on 2009-09-12
At a very base level you could combine each program's main() method into one class and rename them, appropriately to add(), subtract(),etc, e.g.

```

	public static void add(Scanner input)
	{
                System.out.println("Below is a simple sum = number1 + number2 Program \n");

                int number1;
                int number2;
                int sum;

                System.out.print( "Enter First integer: " );
                number1 = input.nextInt(); //Defines number1
                System.out.print( "Enter Second interger: " );
                number2 = input.nextInt(); //Defines number2

                sum = number1 + number2;
                System.out.printf( "Sum equals %d\n", sum);
	}

```

N.B. I've passed in the Scanner as I'm not sure of the behaviour if you have multiple scanners handling the same input.

Then make a simple main to call each method based on the choice:

```

	public static void main(String[] args)
	{
                System.out.println("Select an Application from below: \n");
                System.out.println("(1) Addition");
                System.out.println("(2) Subtraction");
                System.out.println("(3) Multiplication");
                System.out.println("(4) Division \n");
                System.out.println("Choice?:");

                Scanner input = new Scanner( System.in );

                int choice;
                if(choice == 1)
                     add(input);
                // extra ifs or a switch statement go here 
                // to call other methods as appropriate

	}



```

Note that this is a very crude way to achieve your aim...but it should get you moving again....

---

### Post by Dark Aspect on 2009-09-12
Well that made sense, however I get four errors when I compile on the public void lines that says

```
Addition.java:48: illegal start of expression
public void multiplication(){
```

What did I do wrong?

---

### Post by issih on 2009-09-12
you'll need to post more of the source than that, I suspect you have failed to put a closing brace in somewhere (most likely just before that line in the source), but we can't tell you for certain without you posting the whole thing, or at least 10 lines either side.

---

### Post by Dark Aspect on 2009-09-12
> **issih said:**
> you'll need to post more of the source than that, I suspect you have failed to put a closing brace in somewhere (most likely just before that line in the source), but we can't tell you for certain without you posting the whole thing, or at least 10 lines either side.

Heres the whole file along with the compiler errors

```
import java.util.Scanner;

public class test

{
	public static void main(String[] args)
	{
		System.out.println("Hello, from Dark_Aspect");
                System.out.println("Select an application from below: \n");
                System.out.println("(1) Addition");
                System.out.println("(2) Subtraction");
                System.out.println("(3) Multiplication");
                System.out.println("(4) Division");
                Scanner input = new Scanner( System.in );
                int choice = scan.nextInt();
                if(choice == 1){
                    addition();
                }
                else if(choice == 2){
                    subtraction();
                }
                else if(choice == 3){
                    division();
                }
                else if(choice == 4){
                    multiplication();
                }
                else{
                    System.out.println("not and option");
                    }

          public void addition(){
             Scanner input = new Scanner( System.in );
             int number1;
             int number2;
             int sum;

             System.out.print( "Enter First integer: " );
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: " );
             number2 = input.nextInt();

             sum = number1 + number2;
             System.out.printf( "Sum equals %d\n", sum);
                                }
          public void subtraction(){
             Scanner input = new Scanner( System.in );

             int number1;
             int number2;
             int difference;

             System.out.print( "Enter First integer: " );
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: ");
             number2 = input.nextInt();

             difference = number1 - number2;
             System.out.printf( "The difference is %d\n", difference);
                                   }
          public void multiplication(){
             Scanner input = new Scanner( System.in );
             int number1;
             int number2;
             int product;


             System.out.print( "Enter First integer: ");
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: ");
             number2 = input.nextInt();

             product = number1 *number2;
             System.out.printf( "The product is %d\n", product);
                                      }
          public void division(){
             Scanner input = new Scanner( System.in );
             int number1;
             int number2;
             int dividen;

             System.out.print( "Enter First integer: ");
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: ");
             number2 = input.nextInt();

             division = number1 / number2;
             System.out.printf( "Dividen is %d\n", dividen);
                                }
	}
}
```

and the compiler errors:

```
test.java:29: illegal start of expression
          public void addition(){
          ^
test.java:29: illegal start of expression
          public void addition(){
                 ^
test.java:29: ';' expected
          public void addition(){
                              ^
test.java:43: illegal start of expression
          public void subtraction(){
          ^
test.java:43: illegal start of expression
          public void subtraction(){
                 ^
test.java:43: ';' expected
          public void subtraction(){
                                 ^
test.java:57: illegal start of expression
          public void multiplication(){
          ^
test.java:57: illegal start of expression
          public void multiplication(){
                 ^
test.java:57: ';' expected
          public void multiplication(){
                                    ^
test.java:71: illegal start of expression
          public void division(){
          ^
test.java:71: illegal start of expression
          public void division(){
                 ^
test.java:71: ';' expected
          public void division(){
                              ^
12 errors

```

---

### Post by shadylookin on 2009-09-12
well first

```

Scanner input = new Scanner( System.in );
int choice = scan.nextInt();

```

you've created an instance of Scanner class called input yet for some reason in the next line you calling scan. Either make the name input or scan you can't have both. 

Later on when you call division(), addition() etc. It appears I've accidentally mislead you. You either have to create an instance of the Test class or change all those to static. For example

```

Test t = new Test();
t.addition();
t.division();

```

or make all those functions static like this

```

public **static** void addition(){
    //logic
}

```

Next you have to close off your main method before you can declare others. You need another } after that else statement

finally you have 

division = number1 / number2;

at the bottom but you don't have a variable called division.

---

### Post by Dark Aspect on 2009-09-12
Okay it works, all is exactly the way I wanted it.

[IMG]http://img44.imageshack.us/img44/2341/screenshotadministrator.png[/IMG]

For the record if anyone is learning from this, a float works much better than an integer for division. Mostly due to the fact that you can get decimals with floats but it also runs more stable. Heres the source if anyone is interested in playing around.

Thanks, shadylookin and issih.

```
//Integrates the four basic arithmetic applications into a single C.L.U.I program.
import java.util.Scanner;
public class test
{
	public static void main(String[] args)
	{
		System.out.println("Hello, from Dark_Aspect");
                System.out.println("Select an application from below: \n");
                System.out.println("(1) Addition");
                System.out.println("(2) Subtraction");
                System.out.println("(3) Multiplication");
                System.out.println("(4) Division");
                System.out.println("Choice? ");

                Scanner input = new Scanner( System.in );
                int choice = input.nextInt();
                if(choice == 1){
                    addition();
                }
                else if(choice == 2){
                    subtraction();
                }
                else if(choice == 3){
                    multiplication();
                }
                else if(choice == 4){
                    division();
                }
                else{
                    System.out.println("Not an option");
                    }
      }
          public static void addition(){
             Scanner input = new Scanner( System.in );
             int number1;
             int number2;
             int sum;

             System.out.print( "Enter First integer: " );
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: " );
             number2 = input.nextInt();

             sum = number1 + number2;
             System.out.printf( "Sum equals %d\n", sum);
                                }
          public static void subtraction(){
             Scanner input = new Scanner( System.in );
             int number1;
             int number2;
             int difference;

             System.out.print( "Enter First integer: " );
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: ");
             number2 = input.nextInt();

             difference = number1 - number2;
             System.out.printf( "The difference is %d\n", difference);
                                   }
          public static void multiplication(){
             Scanner input = new Scanner( System.in );
             int number1;
             int number2;
             int product;

             System.out.print( "Enter First integer: ");
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: ");
             number2 = input.nextInt();

             product = number1 * number2;
             System.out.printf( "The product is %d\n", product);
                                      }
          public static void division(){
             Scanner input = new Scanner( System.in );
             float number1;
             float number2;
             float dividen;

             System.out.print( "Enter First integer: ");
             number1 = input.nextInt();
             System.out.print( "Enter Second integer: ");
             number2 = input.nextInt();

             dividen = number1 / number2;
             System.out.printf( "Dividen is %f\n", dividen);
                                }
}
//End of File ~ Date 09/12/09

```

---

